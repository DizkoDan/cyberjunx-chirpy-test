---
id: 210
title: "Migration Night Part 1"
date: 2007-09-15T00:08:11-04:00
author: DizkoDan
layout: post
guid: 'http://www.cyberjunx.com/blog/archives/2007/09/15/migration-night-part-1/'
permalink: /2007/09/15/migration-night-part-1/
ljID:
    - '377'
categories:
    - Linux
    - Technology
---

So it’s finally migration night for [serve-you.net](http://www.serve-you.net), and so far things are not starting smoothly. I tried to start the backup, and of course there appears to be a bug in the backup utility, which is supposedly resolved in the next version of Plesk. So I figure I might as well do the upgrade first, since the server I am migrating to is already running the latest version. Of course the upgrade fucking breaks! So now I first have to fix this hozed up upgrade before I can do the backup, migrate the data, then restore it.

It’s gonna be a long night!  
 **Update 12:30AM** My ninja skills are still in tact. Got Plesk mostly working again, backup is now running.

**Update 1:50AM** transfer is going so slow. I’m only getting 1.4MB/s between the two servers, and I have 4.5GB of compressed data to transfer.

**End Game 3:35am** Well, it just wasn’t meant to be tonight. It’s 3:30 in the morning, and the restore has failed twice. Giving up on this attempt, and I’m gonna have to reschedule this damn thing.