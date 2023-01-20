---
id: 43
title: 'Server Woes'
date: '2003-01-30T19:52:00-04:00'
author: DizkoDan
layout: post
guid: 'http://www.cyberjunx.com/blog/?p=43'
permalink: /2003/01/30/server-woes/
ljID:
    - '322'
categories:
    - General
    - Hardware
    - Technology
---

Well as most of you know my webserver which hosts our personal domains, and some friends decided to take a shit last week. It actually started a couple weeks ago when strange noises began to make their way out of this machine. This is usually one of two things, harddrive, or cpu fan. So I chose the weekend to pull the server from the rack and run it opn to verify which it was, and order a new one on Monday. I pull the machine and sure enough, it’s the CPU Fan. I took a big sigh here, cuz a good CPU Fan is only $20 as opposed to about $100 for a new HD. I had an extra fan lying around, so I decided to swap it out in case this one completely died before my replacement would arrive, then I’d be fucked with a fried CPU (see the irony here?). So I shut the bitch down, swap out the fan, plug her back in, hit the power, and NOTHING. The fucker wont post at all.  
<lj text="Read more here">  
After doing the normal diagnostics, I came to the conclusion that it could be one of three things. The CPU, mobo, or power supply. This is some rather old hardware, so I decided why not replace it all, instead of taking chances. So I order a new case w/power supply, CPU, mobo, &amp; fan. Everything arrived yesterday, I load the new case up, power on, and NOTHING. Same problem appears… this essentially new machine wont post. After testing several ways, I come to the conclusion that this is a lost cause, and one of these things is dead again. So I decided to temporarily put stvlive on my development server, until I can get to the bottom of these problems. </lj>

So last night I stayed up way too fuckin late manually setting up stv on this other machine. By morning, I had everything working, when I realized that there were a lot of environmental things that I would have to rebuild on this temp server to make stv completely happy. Like the fact that this machine had no mail server setup, and the server stv lives on has a pretty complex setup that relays to my real mail server, So it hits me that I wasted several hours when I should have just pulled the HD and swapped it into this box. So I make the decision to do that this evening.

After talking to a few people about it today, the only conclusion I can come up with is that maybe the RAM was bad, and was frying out the mobo. Since this was the only thing that hadn’t changed, this seems to make sense. However, I came home this evening, and swapped out the drives and booted up my test server with the drive from the webserver, and all was good. So I decided to try putting some of the aforementioned RAM in it, and see what happens. I put one stick in, no problems. Put another in, again no problems. So this shoots down my theory completely.

The plus side is, the test server is now up and running as the webserver with all sites. And since the RAM is working, it’s loaded up, so the difference in speed should be minimal except when it’s doing heavy duty processing since it’s only a duron compared to the athlon in the webserver. My thoughts now are that I got a bum CPU, and it’s just a strange coincidence. I’m gonna send the CPU back to exchange it, and hopefully this saga will end. If not, I’ll probably just curl up in the fetal postition and cry like a baby for a while. But the webserver should be in good enough shape to keep running on my dev server for the time being.