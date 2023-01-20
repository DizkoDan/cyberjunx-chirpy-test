---
id: 1345
title: 'Using adb'
date: '2010-08-24T19:19:13-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/'
aktt_notify_twitter:
    - 'yes'
---

## What is adb?

adb stands for Android Debug Bridge. In short, it’s a tool that provides you the ability to manage your android device through a console on your computer. With adb, you can execute shell commands on your device &amp; copy files to/from it.

## Installing adb

adb is part of the [Android SDK](http://developer.android.com/sdk/index.html). Rather than rehash the install steps, I’m going to refer you to my [rooting guide](http://www.cyberjunx.com/blog/android/hacking/rooting/), which outlines the SDK install.

## Using adb

Open a CMD Prompt (or terminal on linux/mac), and cd into your sdk directory/tools. Type adb, and it will output a list of available commands. There are a lot of options/commands, but I’ll outline a few of the most common here. Since android is linux, most of the commands you would expect are there when using the shell (ls, cd, cp, mv, rm, etc).

7. **adb devices** – Use this command to verify that your device is connected. If it does not show up
8. a**db push FILENAME** – This will copy a file or directory from your computer to your device.
9. **adb pull FILENAME** – This will copy a file or directory from your device to your computer.
10. **adb shell** – This opens an interactive shell on your device.
11. **adb shell COMMAND** – This will execute a command.
12. **adb install SOMEPACKAGE.apk** – This will remotely install an android package on your device.
13. **adb uninstall SOMEPACKAGE.apk** – This will remove a package from your device.
14. **adb reboot recovery** – This will reboot the device into recovery.
15. **adb reboot bootloader** – This will reboot the device into HBOOT.
16. **adb logcat** – This will view the logfiles on the device. You can feed this several filtering options.