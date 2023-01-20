---
id: 1371
title: Unroot
date: '2010-08-25T22:07:33-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/'
aktt_notify_twitter:
    - 'yes'
---

There may come a time when you need to unroot and revert to stock. I know, I know… hold back your tears. The good news is, it’s possible. The bad news is, if you’ve flashed your radio, it’s a bit more difficult. However, it’s still a pretty simple process. Obviously, this will wipe out all apps &amp; data, so make a backup if you care about anything. I’d recommend downloading an app called [MyBackup](http://www.appbrain.com/app/com.rerware.android.MyBackup) to your phone, and do a full backup of apps &amp; data, since you can’t use [Titanium Backup](http://www.appbrain.com/app/com.keramidas.TitaniumBackup) after you unroot.

My standard disclaimer applies.

<font color="red">**DISCLAIMER: Hacking your device will void your warranty, and can be dangerous. You may end up with a “bricked” device if anything goes wrong. I take no responsibility if something happens to your device. If you are ever in doubt STOP! This is not something to take lightly.**</font>

## If you **HAVE** updated your radio, **AND** installed unr**evo**ked forever on 2.2

1. Make sure that your SD card is formatted FAT32. Download [this PB31IMG.zip](http://adrynalyne.us/files/ruu/2.2/PB31IMG.zip) (Thanks Adrynalyne) which contains all parts needed to get you stock (minus changing S-off back) to the root of your SD card. 2\. Boot into HBOOT, by powering the phone down, then booting back up holding the Volume Down + Power buttons.

3\. The phone should see the img, and ask you if you want to update. Say yes.

4\. That’s all.


## If you have **NOT** updated your radio, and are on 2.1

1. Make sure that your SD card is formatted FAT32. Download the 2.1 stock RUU PB31IMG.zip to the root of your SD card (you can find this on xda). 2\. Boot into HBOOT, by powering the phone down, then booting back up holding the Volume Down + Power buttons.

3\. The phone should see the img, and ask you if you want to update. Say yes.

4\. That’s all.


## If you **HAVE** updated your radio, **AND** installed unr**evo**ked forever on 2.1

1. Make sure that your SD card is formatted FAT32. Download [this PB31IMG.zip](http://adrynalyne.us/files/ruu/2.1/PB31IMG.zip) (Thanks Adrynalyne) which contains all parts needed to get you stock (minus changing S-off back) to the root of your SD card. 2\. Boot into HBOOT, by powering the phone down, then booting back up holding the Volume Down + Power buttons.

3\. The phone should see the img, and ask you if you want to update. Say yes.

4\. That’s all.


## If you **HAVE** updated your radio, but did NOT use unr**evo**ked forever

1. Download the zip in [this thread](http://androidforums.com/incredible-all-things-root/99828-video-howto-unroot-incredible-downgrading.html) (there’s also a great video there) to your computer and extract the flash\_image &amp; mtd0.img files to your sdk tools directory. See my [rooting guide](http://www.cyberjunx.com/blog/android/hacking/rooting/) if you don’t know what this is. 2\. [Boot into recovery](http://www.cyberjunx.com/blog/android/hacking/recovery/)

3\. In recovery, go to mounts and storage, then select mount /system

4\. Connect your phone to your computer and [open adb](http://www.cyberjunx.com/blog/android/hacking/using-adb/)

5\. Execute the following commands:  
`<br></br>adb push flash_image /data<br></br>adb push mtd0.img /data<br></br>adb shell<br></br>chmod 777 /data/flash_image<br></br>cd /data<br></br>flash_image misc mtd0.img<br></br>exit<br></br>adb reboot oem-78<br></br>`

6\. When you see the silver HTC screen go ahead and pull your battery to shutdown.

7\. Make sure that your SD card is formatted FAT32. Copy PB31IMG.zip to the root of your SD card (This should have been in the download from step 1).

8\. Boot into HBOOT, by powering the phone down, then booting back up holding the Volume Down + Power buttons.

9\. The phone should see the img, and ask you if you want to update. Say yes.

10\. That’s all.