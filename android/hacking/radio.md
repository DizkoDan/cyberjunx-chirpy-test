---
id: 1312
title: 'Flash Your Radio'
date: '2010-08-21T14:14:02-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/'
aktt_notify_twitter:
    - 'yes'
---

A radio update generally adds increased range, or unlocks certain features on the radio/antenna chipset. On the Incredible, the 2.x radio’s will add 720p video, &amp; wireless N. In the past, if you wanted to install a new radio, it was recommended to do it before rooting, as you had to use the stock HBOOT. This has changed with the release of [unr**evo**ked forever](http://www.cyberjunx.com/blog/android/hacking/unrevoked-forever/). This is now the preferred method. That said, please read the warnings on our page, since as of the time of writing, there is no way back once you install [unr**evo**ked forever](http://www.cyberjunx.com/blog/android/hacking/unrevoked-forever/).

<font color="red">**DISCLAIMER: Updating your radio will void your warranty, and can be dangerous. You may end up with a “bricked” device if anything goes wrong. While it can be reversed, it is a fairly complex procedure. I take no responsibility if something happens to your device. If you are ever in doubt STOP! This is not something to take lightly.**</font>

### If you have installed [unr**evo**ked forever](http://www.cyberjunx.com/blog/android/hacking/unrevoked-forever/)

1\. Make sure that your SD card is formatted as FAT32. Download the radio to the root of your SD card (I will not post the radios here, because they are proprietary. You can find them on XDA). Leave the file named as PB31IMG.zip.

2\. Boot into HBOOT, by powering the phone down, then booting back up holding the Volume Down + Power buttons.

3\. Once it boots into HBOOT, if you did not rename the file to something other than PB31IMG.zip, it will automatically scan it and ask you if you want to apply the update. Hit yes.

4\. When prompted, say yes to reboot.

5\. Once booted into the OS, go to Settings-&gt;About Phone-&gt;Software-&gt;Software Information, and verify that your Baseband Version matches the Radio you just installed. You should remove PB31IMG.zip from your SD card now.


### If you HAVE NOT installed [unr**evo**ked forever](http://www.cyberjunx.com/blog/android/hacking/unrevoked-forever/) &amp; choose not to

\* Note that you can only install the 2.05 radio if you do not use [unr**evo**ked forever](http://www.cyberjunx.com/blog/android/hacking/unrevoked-forever/). DO NOT attempt to install the 2.15 radio.

#### If you are rooted, you must first unroot by following these instructions.

1\. Make sure that your SD card is formatted as FAT32. Download the 1.00 PB31IMG.zip and place it in the root of you SD card (I will not post the radios here, because they are proprietary. You can find them on XDA).

2\. Boot into HBOOT, by powering the phone down, then booting back up holding the Volume Down + Power buttons.

3\. Once it boots into HBOOT, if you did not rename the file to something other than PB31IMG.zip, it will automatically scan it and ask you if you want to apply the update. Hit yes.

4\. When prompted, say yes to reboot.

5\. You are now completely stock. You should remove PB31IMG.zip from your SD card now.


#### For unrooted phones, follow these steps to install the 2.05 radio.

1\. Make sure that your SD card is formatted as FAT32. Download dinc\_ota.zip, rename it to update.zip and place it in the root of your SD card (I will not post the radios here, because they are proprietary. You can find them on XDA).

2\. [Boot into Recovery](http://www.cyberjunx.com/blog/android/hacking/recovery/)

3\. When you see the red exclamation point, hole the Volume Up + Power Button.

4\. Select apply update.zip

5\. Go to Settings &gt; About phone &gt; Software information &gt; Baseband version and verify that it’s 2.05.00.06.11. You should remove the update.zip from your SD card now.

6\. You probably want to [re-root](http://www.cyberjunx.com/blog/android/hacking/rooting/) and go [install your favorite ROM](http://www.cyberjunx.com/blog/android/hacking/roms/) now!