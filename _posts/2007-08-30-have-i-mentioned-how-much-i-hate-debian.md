---
id: 203
title: "Have I mentioned how much I hate Debian?"
date: 2007-08-30T22:03:04-04:00
author: DizkoDan
layout: single
guid: 'http://www.cyberjunx.com/blog/archives/2007/08/30/have-i-mentioned-how-much-i-hate-debian/'
permalink: /2007/08/30/have-i-mentioned-how-much-i-hate-debian/
ljID:
    - '370'
categories:
    - Hardware
    - Linux
    - Technology
---

So we landed a fairly big customer. Said customer is all about Debian. It went down kind of like this

Sales: “Will you guys support 40 Debian servers?”  
Us: “No!”  
Sales: “Okay, we’ll need those by the end of September”

So of course not only am I the guy responsible for creating all Linux deployments, I’m one of the only people in the company that know anything about it. I’ve never been a fan of Debian. I’ve tried to like it, and it just never works out. Talk all the shit you want about Red Hat based distros, but there’s a reason they rule the corporate Linux marketplace.

So anyway, now I have to figure out a way to integrate Debian into my kickstart server, or create another deployment server using their lame ass FAI. And did I mention that said deployments will be happening on blades that HP completely does not support Debian on? Should be fun trying to find modules for this shit, let alone managing these servers after the install.