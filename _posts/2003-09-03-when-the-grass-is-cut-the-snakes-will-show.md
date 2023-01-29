---
id: 23
title: "When the grass is cut the snakes will show"
date: 2003-09-03T10:14:00-04:00
author: DizkoDan
layout: post
guid: 'http://www.cyberjunx.com/blog/?p=23'
permalink: /2003/09/03/when-the-grass-is-cut-the-snakes-will-show/
ljID:
    - '337'
categories:
    - General
    - Hardware
    - Linux
    - Technology
---

Note to self.. Mail server is cursed.

Just a few weeks ago, I had to completely rebuild my mail server due to a hozed HD. Things were running smooth, and I had managed to get all kinds of shit working that I had been meaning to for a while. Fast forward to Monday night.

Got to work at about 10:30pm and tried to ssh into my mail server. Immediately it returned a connection terminated. So I had Steph go look at the console, and sure enough, it had a kernel panic. She rebooted it, and it did it again. Rebooted again, seemed to be okay. I start investigating the panics, and come to the conclusion that it’s probably bad RAM or the swap partition iz fux0red. As I’m looking around, I get some dma errors (a sign of a dying HD). So when I got home in the morning, I brought the server down to test the RAM. All tested fine. The HD however, told me to go take a flying fuck!

So I spent several hours attempting to clone the drive, but it was too far gone, and kept crashing on me. Finally at about 5:00pm I gave up and went to sleep. I woke up at about 3:00am and started a clean install. Luckily I was able to mount the old HD, and copy the maildir’s, and important configs, so everything seems to be in order now.

Covad got dispatched out again today. Even after I tried to explain to the dispatcher that my DSL was up, just not at the right speed. So when the d00d showed up this morning, I was like go away, and fix my shit at the DSLAM! With any luck this will be closed out today.

Aside from that, I’m working on a migration process to move serve-you.net to a new datacenter. Meanwhile Steph seems to be dying from ebola or some shit.