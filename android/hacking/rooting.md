---
id: 1257
title: Rooting
date: '2010-08-20T09:54:56-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/'
aktt_notify_twitter:
    - 'yes'
---

## What and Why?

**What does “rooting” mean?**  
In short, it means to gain root (admin) privileges in the operating system. Since android is based on linux, the admin user is “root”. Thus the term “rooting”.

**Why would you want to root your phone?**  
Only you can answer this for yourself, but here’s a few reasons why I chose to do so.

4. Being able to backup/restore apps and data at the system level
5. Being able to take screenshots
6. Getting rid of all the useless crap that is installed by my carrier
7. Installing different versions of the OS (can you say Froyo?)
8. Installing custom kernels (overclocking, better battery life)
In case you didn’t read my warning on the previous page, here it is again.

<font color="red">**DISCLAIMER: Rooting your phone will void your warranty, and can be dangerous. You may end up with a “bricked” device if anything goes wrong. I take no responsibility if something happens to your device. If you are ever in doubt STOP! This is not something to take lightly..**</font>

**Additional note. While rooting is reversible, it’s not something you should ever plan to do. If you take a look at any of the android forums right now, you’ll see post after post like “how to get the ota”, “how to unroot”, “the ota wont work on my rooted phone”. Use some common sense here. If you don’t understand the consequences what you are doing, DO NOT ROOT YOUR PHONE! You have been warned.**

Since I have an Incredible, most of my information is geared towards that device. The method that I use can be used on some other devices as well, and the steps are the same. Also note that there are other ways to accomplish this. These directions are for Windows, since it’s the most common.

## Using [unr**evo**ked ](http://unrevoked.com/)to root.

<font color="red">**Note:** As of unr**evo**ked 3.2, S-OFF ([unr**evo**ked forever](http://www.cyberjunx.com/blog/android/hacking/unrevoked-forever/)) is included by default.</font>

unr**evo**ked3 makes it easier than ever to root your phone. You need a few things to get started.

1. Download the [android SDK](http://developer.android.com/sdk/index.html) to your computer. 2\. Download the [unr**evo**ked recovery](http://unrevoked.com/recovery/) tool to your computer.

3\. Download the [android USB driver](http://www.unrevoked.com/rootwiki/lib/exe/fetch.php?hash=908951&media=http%3A%2F%2Fwww.unrevoked.com%2Frecovery%2Fandroid-usb-driver.zip) to your computer.

4\. I’d recommend downloading an app called [MyBackup](http://www.appbrain.com/app/com.rerware.android.MyBackup) to your phone, and do a full backup of apps &amp; data, since you can’t use [Titanium Backup](http://www.appbrain.com/app/com.keramidas.TitaniumBackup) until you have rooted.

5\. If you have installed the HTC Sync crap, you need to uninstall it, as it’s known to conflict. You can reinstall it later if you use it.


Once you have these files you are ready to begin.

1. To install the android SDK, simply unzip the package, and move the android-sdk-windows somewhere easy to get to from a cmd prompt. I like to move it to the root of c:\\. You can rename it something like SDK if you like as well. Open that folder, and execute the SDK Manager.exe. You only need to install the USB Drivers (The SDK Tools are automatically installed). It will pre-populate the installer with a bunch of stuff. Just click each one that has a green check, then hit reject. Hit install once you have only the USB driver checked. 2\. Extract your android USB drivers (that you downloaded in step 3 of the prep) in your android SDK folder. You can replace the existing USB drivers there.

3\. Execute the unr**evo**ked recovery executable. This just extracts the files where you tell it, it’s not actually installing anything yet.

4\. On your phone, go to Settings-&gt;Applications-&gt;Development and enable USB Debugging.

5\. Make sure your phone is set to “charge only” in Settings-&gt;Connect To PC-&gt;Default connection type

6\. Connect your phone to your computer.

7\. Turn off your phone, then boot it into the HBOOT menu by holding **power** and **volume down**.

8\. Open up Device Manager and look for your phone. Right Click on it, and click update driver. Select browse my computer for software. Browse to the directory that you extracted your USB drivers to, click ok (make sure to select include subfolders), click next. You should see it find and install the driver. Click ok, and you should now see the Android Bootloader Interface.

9\. Reboot your phone normally, and connect it to your computer.

10\. Open the folder where unr**evo**ked extracted (in step 3), and run reflash.exe An installer window will open and you simply follow the prompts. Once it’s finished, the installer window will remain open, but it will say “Done” in the status.

11\. At this point you are officially rooted, and your phone should be sitting in the ClockworkMod Recovery. You can disconnect from the computer and reboot back into the OS at this point.


Now that you are rooted, your first order of business should be to do a [nandroid backup](http://www.cyberjunx.com/blog/android/hacking/nandroid-backups/) of your “virgin” phone.