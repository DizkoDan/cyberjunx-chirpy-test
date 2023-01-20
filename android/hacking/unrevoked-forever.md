---
id: 1318
title: 'unrevoked forever'
date: '2010-08-21T14:41:19-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/'
aktt_notify_twitter:
    - 'yes'
---

<font color="red">**DISCLAIMER: This will void your warranty, and can be dangerous. You may end up with a “bricked” device if anything goes wrong. I take no responsibility if something happens to your device. If you are ever in doubt STOP! This is not something to take lightly.**</font>

What is unr**evo**ked forever?

Straight from their [site](http://unrevoked.com/rootwiki/doku.php/public/forever):

> unr**evo**ked forever is a tool to set your Android phone’s security level to S-OFF. The security level is a flag stored on the radio; when the flag is S-OFF, the bootloader (HBOOT) will no longer check the signatures of firmware images before flashing them. This allows custom firmware images to be uploaded, including unsigned boot, recovery, splash1, and hboot images (as well as official images that have been modified). When the system is S-OFF, the NAND flash memory protection is also reduced; this allows all partitions (including /system) to be written to while the operating system is booted.
> 
> The most substantial benefit of unrevoked forever is that the change is stored in the radio’s NV memory; no ENG bootloader is necessary to continue to flash firmware images. Even if an “unrootable” OTA update is accepted, a device on which unrevoked forever has been run will still be able to reflash a custom recovery image.

## To install unr**evo**ked forever (S-OFF) on your phone.

<font color="red">**Note:** If you used unr**evo**ked 3.2 or higher, S-OFF is already set. Follow step 5 to validate.</font>

1\. If your phone does not already have a custom recovery, use [unr**evo**ked3 to root your phone](http://www.cyberjunx.com/blog/android/hacking/rooting/).  
The installation process cannot take place if the phone does not have a custom recovery installed.

2.Download the most recent ”[unrevoked-forever.zip](http://downloads.unrevoked.com/forever/current/unrevoked-forever.zip)” to the root of your SD card.

<font color="red">**Did you read the important safety information above?  
Do so now before continuing.**</font>

3\. The update can be installed like any custom .zip file. Simply [flash it from your custom recovery](http://www.cyberjunx.com/blog/android/hacking/roms/).

4\. Review the output to determine if there were any errors.  
If messages beginning in E: appear, stop! If possible, join IRC for support.

5\. Restart the phone normally, then reboot the phone into the bootloader. This can be done by holding VOLUME DOWN while powering the system up. Observe at the top that S-OFF appears.

6\. Optional: show your support (and your S-OFF bootloader) by [flashing a custom splash screen](http://unrevoked.com/rootwiki/doku.php/public/forever#custom_splash)!


If you ever need to change this back, say for warranty return, good news! The unr**evo**ked team has now released a tool to reverse this!

## To remove unr**evo**ked forever (S-ON)

1\. Download [this file](http://downloads.unrevoked.com/forever/current/unrevoked-forever-son.zip) to the root of your SD card.

2\. Install like any custom .zip file. Simply [flash it from your custom recovery](http://www.cyberjunx.com/blog/android/hacking/roms/).

4\. Review the output to determine if there were any errors.  
If messages beginning in E: appear, stop! If possible, join IRC for support.

5\. Restart the phone normally, then reboot the phone into the bootloader. This can be done by holding VOLUME DOWN while powering the system up. Observe at the top that S-ON appears.