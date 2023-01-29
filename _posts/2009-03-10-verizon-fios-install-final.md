---
id: 873
title: "Verizon FIOS Install Final"
date: 2009-03-10T10:27:15-04:00
author: DizkoDan
layout: single
guid: 'http://www.cyberjunx.com/blog/?p=873'
permalink: /2009/03/10/verizon-fios-install-final/
aktt_notify_twitter:
    - 'yes'
ljID:
    - '854'
ljxp_comments:
    - '0'
ljxp_privacy:
    - '0'
categories:
    - General
    - Home
    - Intarwebz
    - Technology
tags:
    - Fibre
    - FIOS
    - Internet
    - Verizon
---

So Verizon was scheduled for the final install from 1-6 on Friday 3/6. I got a call from the installer just before 1:00 on Friday saying he was on his way. He showed up about 10 minutes later, and I showed him where things were, and how I wanted the install done.

I originally thought that there was cable that needed to be run from the ONT (Optical Network Terminal – the box outside which converts fibre to ethernet or coax), inside. The tech told me that the only cable that needed to be run was the power line, which gets hooked up to a UPS inside. They simply use existing wiring to connect you if it’s up to par.

I thought we’d be able to just put the UPS on the wall opposite the ONT in the semi-finished basement, but that proved to be more challenging than expected. We tried fishing the cable through the hole where the rest of the cables come into the house, but could not find them on the other side. I started pulling up the paneling to see if I could find the cable, but it would have meant taking down half a wall of paneling plus the trim, so we aborted that plan.

After looking around for a while, and me shooting down his ideas to put the unit on the second floor, in the bathroom or kitchen, I remembered that the directv installers drilled a hole in the middle of the house going down to the basement. After figuring out where those cables went, and how to route them from the ONT, we were in business.

After the power cable was run, the UPS unit was installed in my utility room, which is much better than where I originally planned, since I eventually want to redo that room, and would have to move it. After that, we used the existing coax cable that my comcast router was connected to, and connected that to the ONT on the outside, and the Actiontec MI424WR router that Verizon provided.

I asked if it was possible to not use their router (which btw, isn’t a bad router, my d-link is just a lot better), but unfortunately, the installer could not do that. It would require that ethernet be run from the ONT, so that wasn’t going to happen. He did however say that I could just turn it into a bridge, though he wasn’t allowed to do that for me. Fine by me!

It took a couple of minutes for him to get the circuit activated, then he flashed the router, and we were up and running. I did a few non biased speedtests on speedtest.net, and the speed was about as good as could be expected (just under 20 down and about 4.5 up). I was satisfied, so I sent him on his way.

I immediately hopped on the actiontec router to reconfigure it as a bridge, but was overwhelmed by the dumbed down interface. A quick google search, and I was armed with the info I needed. 5 minutes later, the wifi on the actiontec was disabled, and the router was in bridge mode. An IP release/renew on my wireless router was all it took for all my systems to be back online.

I did a few tests from various computers to make sure all was well. I noticed that one of the cams wasn’t uploading to [stvlive.com](http://www.stvlive.com), and at first I just thought it was that retarded old mac mini acting up. However, the intarwebs were working in other programs. I checked Steph’s desktop, and sure enough, none of the cams there were uploading either. In a stroke of luck, someone had complained a couple of days earlier that they were having trouble accessing [stvlive.com](http://www.stvlive.com) from a Verizon connection. So I tried to SSH to the server, and sure enough, I couldn’t reach it. So I SSH’d in from another server, and found that the entire class A was being blocked by the firewall as a “reserved network”. I removed the subnet, and boom! All was well.

Overall, I am very pleased with the service so far. The speed has been impressive, and stable from the little bit of time that I have used it. The real test will come when Steph has to upload one of her gigantic PSD’s to our servers. If she’s happy, then I’ll be happy.