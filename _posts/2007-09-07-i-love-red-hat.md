---
id: 208
title: 'I love Red Hat'
date: '2007-09-07T14:25:11-04:00'
author: DizkoDan
layout: post
guid: 'http://www.cyberjunx.com/blog/archives/2007/09/07/i-love-red-hat/'
permalink: /2007/09/07/i-love-red-hat/
ljID:
    - '375'
categories:
    - General
    - Hardware
    - Linux
    - Technology
---

Yesterday afternoon I found out we signed yet another customer wanting a non-standard OS. These guys want Fedora. While it pissed me off that they once again dropped this on my plate, without consulting me first, I wasn’t too worried, as I knew I could make Fedora work with my current kickstart server easily. How easy? Within an hour of being told this customer was signed, I had the iso’s downloaded, extracted to my kickstart server, kickstart config built, and a working deployment to one of my blades! The only thing that didn’t work right off was the Proliant Support Pack, which is to be expected, since I think HP hard codes OS versions in the installer. It was a nice break from the Debian nonsense and a small victory of sorts for me.

As for Debian, I finally had a successful install on a blade this morning. I got the Proliant Support Pack .deb’s from HP installed, and I even got the Altiris agent installed. Believe it or not, the server actually checked into altiris, and I can manage it. This is huge! So I made an image of the server from altiris, and deployed it to another blade. Unfortunately there’s issues there that I need to figure out. But I’m pretty happy I finally got an successful install.

On a side note, while looking into the Fedaora PSP install failure, I figured out something that I’ve been looking for since April.