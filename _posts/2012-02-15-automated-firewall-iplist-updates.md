---
id: 1626
title: "Automated firewall iplist updates"
date: 2012-02-15T10:53:54-04:00
author: DizkoDan
layout: single
guid: 'http://www.cyberjunx.com/blog/?p=1626'
permalink: /2012/02/15/automated-firewall-iplist-updates/
aktt_notify_twitter:
    - 'yes'
tc-thumb-fld:
    - 'a:2:{s:9:"_thumb_id";b:0;s:11:"_thumb_type";s:10:"attachment";}'
categories:
    - Linux
    - Technology
tags:
    - csf
    - linux
    - monitoring
    - pingdom
    - scripts
    - serve-you.net
---

So I’ve used [pingdom](http://www.pingdom.com "Pingdom") for years to monitor servers/services related to my hosting business [www.serve-you.net](http://www.serve-you.net "www.serve-you.net"). They offer a great service at a reasonable price, so I don’t have to setup my own monitoring hosts. They have tons of monitoring servers around the globe, which is a good way to not only monitor the up/down status, but also latency/page load times, etc.

The problem I often have though, is that monitoring servers are added/removed fairly often. I usually have pretty strict firewall rules on my servers, so allowing these servers is a must, since the activities that they perform is often seen as an attack. Pingdom publishes a list of active servers in the control panel, but keeping up with this and manually updating my firewall rules (I use [CSF](http://www.configserver.com/cp/csf.html "CSF") on my cPanel servers) can be a pain. Luckily Pingdom also has an [RSS feed](https://www.pingdom.com/rss/probe_servers.xml "RSS feed") with the server list, though it’s in XML format of course. So I finally got around to setting up a script to automate updating the firewall rules daily with this list.

Some quick research on this subject found that CSF has a variable in it’s config called `GLOBAL\_ALLOW` that allows you to feed LFD a list of IP’s via a URL. This is great! However, it requires the list to be in plain text, with one IP per line. As I stated above, the list provided by Pingdom is an XML file, so of course this needs to be massaged in order to be fed to CSF directly.

```bash
# The follow Global options allow you to specify a URL where csf can grab a
# centralised copy of an IP allow or deny block list of your own. You need to
# specify the full URL in the following options, i.e.:
# http://www.somelocation.com/allow.txt
#
# The actual retrieval of these IP's is controlled by lfd, so you need to set
# LF_GLOBAL to the interval (in seconds) when you want lfd to retrieve. lfd
# will perform the retrieval when it runs and then again at the specified
# interval. A sensible interval would probably be every 3600 seconds (1 hour).
# A minimum value of 300 is enforced for LF_GLOBAL if enabled
#
# You do not have to specify both an allow and a deny file
#
# You can also configure a global ignore file for IP's that lfd should ignore
LF_GLOBAL = "0"

GLOBAL_ALLOW = ""
GLOBAL_DENY = ""
GLOBAL_IGNORE = ""

```

So I wrote a quick and dirty script which grabs the RSS feed, pulls the IP’s only, and puts them in a file with one IP per line. I then take this list and copy it to a location on a web server, and set the GLOBAL\_ALLOW to get this once a day. Success! Next step was to automate it via cron, and make sure that we have a backup list (I setup 5 backups, in case I don’t notice right away).

The crontab entry:  
`45 23 * * * /root/scripts/update_pingdom_ips.sh >/dev/null 2>&1`

The script:  
```bash
#!/bin/bash
# Grab the latest pingdom monitoring IP's from their RSS feed, and translate them to IPLIST for CSF/LFD.
#
DATE=`date +%d%b%Y-%H%M`
MAX_BACKUPS=5

cd /root/pingdom  
mv pingdom\_ips pingdom\_ips-$DATE

DONE=0  
until \[ $DONE -eq 1 \]  
do  
 FILES=`ls -1rc`  
 TOTAL\_FILES=`echo "$FILES" | wc -l`

 if \[ $TOTAL\_FILES -gt $MAX\_BACKUPS \]  
 then  
 OLD\_FILES=`echo "$FILES" | head -1`  
 rm $OLD\_FILES  
 else  
 DONE=1  
 fi  
done

wget https://www.pingdom.com/rss/probe\_servers.xml -O /root/probe\_servers.xml -o /dev/null  
cat /root/probe\_servers.xml | grep IP | sed -e 's/.\*IP: //g' | sed -e 's/; Host.\*//g' | grep -v IP &gt; /root/pingdom/pingdom\_ips  
rm /home/dan/www/pingdom\_ips  
cp /root/pingdom/pingdom\_ips /PATH/TO/WEBROOT/pingdom\_ips
```
