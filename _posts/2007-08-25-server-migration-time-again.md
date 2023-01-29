---
id: 186
title: "Server migration time again"
date: 2007-08-25T10:32:41-04:00
author: DizkoDan
layout: single
guid: 'http://www.cyberjunx.com/blog/?p=186'
permalink: /2007/08/25/server-migration-time-again/
ljID:
    - '306'
categories:
    - General
    - InfoSec
    - Linux
    - Technology
---

Over the past month or so, I have been working on a flurry of updates, reconfigurations, migrations of services, and entire servers for my personal sites, and my [hosting company](http://www.serve-you.net). The personal stuff is always fairly painless. If something breaks, it’s not the end of the world. We lose a little ad revenue, and a few people complain that they can’t reach [Stvlive](http://www.stvlive.com), or [QuizMeme](http://www.quizmeme.com). I’m a bit of a masochist in this regard, because I always seem to do 8 million projects at once when I should really be focusing on one. In all, I have done, or am in the process of doing 2 complete server migrations (move from one server to another in a completely different Data Center, new IP space, etc), migration of secondary mail &amp; DNS services for my personal sites to a 3rd party, and massive amounts of hardening across all of my sites/servers.

Most of the personal stuff has gone well, and we even revamped some really old stuff on some of the sites, which makes me happy from an InfoSec stand point. I’m mostly content with how things are running on all of those servers, now it’s just the ongoing issues of cleaning things up that have been around since the late 90’s to make things more secure.

My hosting migration however, makes me lose sleep. I have done this a few times over the years, and it usually goes “okay”, but never without some screwup that keeps me up for hours fixing. The problem isn’t from a lack of planning, or skill. I have been doing this a long time, and I am very knowledgeable about these things. Where the problems occur is usually in the little configuration changes (read: hacks) that have been made on the servers over the years, and have been forgotten about. This server has essentially been upgraded and migrated over and over again since 2001. It’s gone through 3 different FULL RedHat releases starting with RedHat 7.1 (going on a 4th now). I can’t even count the number of Plesk versions, I’m an old school customer, so this server (in it’s original form at my house 7 years ago) started at PSA 2.5, and is getting ready to be Plesk 8.2. So as anyone with any admin experience can imagine, the number of “hacks” that would have been put into place over the years to add support for some unsupported feature, or fix a bug. The irony is, that it’s the old “hacks” that were meant to fix something in the past, that break something on the new.

At this point I have most of the behind the scenes work completed. New server is up and running, and has been (mostly) configured. DNS is going to be the biggest hurdle. The current setup is not so good. All DNS is served from the same server. This isn’t really a big deal, because it’s pretty much an all-in-one server, so if DNS goes down, chances are everything else is down too, so the DNS doesn’t really get you anywhere. However, in a migration situation, having a secondary somewhere else is extremely useful because it isn’t going to change. So when the madness happens when I change my name servers at the registry level, propagation isn’t that big of a deal, because the secondary server is still churning out results. So I want to get this server added for all the domains prior to the move.

I host over 200 domains, and unfortunately they were not all registered through me. That means that the owners of all of those domains need to log into their registrar account, and make modifications to their name servers. This is a very simple task for someone with only a little technical knowledge. All of the registrars have documentation on how to do it. The problem is, getting the domain owners to ACTUALLY MAKE THE CHANGE! I am willing to bet most of my customers don’t even know what a registrar is, let alone which one their domain is registered at. Which is going to equal me doing a shit ton of whois lookups for people to point them in the right direction. And in more than a few cases, I’ll probably just have to obtain their login info, and make the change for them. I am actually having some new flash demos made up right now to show people how to login to the various registrars, and make this change, so hopefully that will help a bit. The plus side is, most registrars don’t require an IP address for name servers, so when I actually re-IP my name servers, there shouldn’t need to be any changes on the end user side.

I’m rambling, and I’m sure this is way more information than most people who read my blog care about, but that’s what a blog is for right?