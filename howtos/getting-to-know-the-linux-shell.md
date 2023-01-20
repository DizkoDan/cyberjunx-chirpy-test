---
id: 197
title: 'Getting To Know The Linux Shell'
date: '2007-08-26T00:50:04-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/howtos/getting-to-know-the-linux-shell/'
---

Whenever I am helping users with problems in Linux, I find that one of  
the biggest problems is that users are not always proficient with basic  
commands in a shell. Knowing what to type, and when, can save you tons  
of time and/or money. In an age where GUI frontends are king, a lot of  
sysadmins never learned what we take for granted. Personally, I still  
learn new commands/techniques almost daily. In this “tutorial”, I will  
attempt to lay out some of the most common commands and some basic  
usage, in hopes that even one of these commands could help you.

When I started using Linux, I had a friend who I considered to be a  
ninja! He taught me a ton of stuff, as I dove in head first and started  
my first Linux webserver. This is the stage that I like to call “knows  
enough to be dangerous”. I really had no idea what I was doing. I knew  
a handful of basic commands, and the gui management tools that exist  
now, were virtually non-existent. So as I started messing with  
compiling kernels, modules, and programs, I would always find myself  
with a broken server, and no idea where to begin troubleshooting or  
fixing it. I would call my friend on the phone, and say “Help! My  
server wont boot!” or some other silly problem, and he would spew out  
some commands for me to type, find the problem, and fix it in no time.  
As time went on, I learned from each of these problems.

Today, this is not the case. I find that most people are introduced to  
Linux as a pretty desktop system, and have little exposure to the  
shell. RPM’s have come a long way, to provide a solid package without  
the need of compiling everything from the kernel, to Apache. The  
management tools available now, can do almost everything for you as  
well. Take that a step further, with the introduction to server control  
panels such as webmin, and hosting control panels such as Plesk, and  
some admins may never see a shell at all!

So enough rambling on, let’s get started! All commands will be written in **bold**. I will prepend an actual usage string with **root@hostname &gt;**.  
I’m using root here, because you can see more, and that’s what you are  
usually logged in as when administering the system. However, most  
commands will work as any user (barring permissions).

## man

The first and most important command out there is **man**. Man pages  
are help files for programs. They tell you the syntax of a command, and  
often contain examples. Some are very basic, others can be like reading  
a book. Whenever you need to know how to use a command try typing man  
. Example:  
**root@hostname &gt; man man** man(1)  
man(1)

NAME  
 man – format and display the on-line manual pages  
 manpath – determine user’s search path for man pages

SYNOPSIS  
 man \[-acdfFhkKtwW\] \[–path\] \[-m system\] \[-p string\] \[-C config\_file\]  
 \[-M pathlist\] \[-P pager\] \[-S section\_list\] \[section\] name …  
———

## ls

The **ls** command is used to list files or directories. **ls** surprisingly has a lot of options. In it’s most basic form, with no options, **ls**  
will simply list all files &amp; directories in the current directory.  
It will not list hidden (dot-files) files. If you normally work from  
inside a desktop environment such as KDE or GNOME, knowing how to use **ls**  
will save you from having to use a bulky file manager to view the files  
in a directory. And of course it is essential when working via console  
or remote connection. Some examples:

List all files in a directory including hidden (dot-files) files:  
**root@hostname &gt; ls -a**  
. aquota.user bin etc lib mnt proc tmp  
.. .autofsck boot  
home lost+found opt root usr  
backupz dev initrd misc sbin var

That’s nice, but how do we find out what is actually a file vs a directory?  
**root@hostname &gt; ls -al**  
total 290  
drwxr-xr-x 20 root root 4096 Jul 13 07:47 .  
drwxr-xr-x 20 root root 4096 Jul 13 07:47 ..  
-rw——- 1 root  
root 18432 Jul 13 11:24  
aquota.user  
-rw-r–r– 1 root  
root  
0 Jul 6 18:09 .autofsck  
drwxr-xr-x 8 root  
root 4096 May 23 12:51  
backupz  
drwxr-xr-x 2 root  
root 4096 Jun 15 23:03  
bin  
drwxr-xr-x 4 root  
root 2048 Jul 3  
23:49 boot  
drwxr-xr-x 22 root root 118784 Jul 6 18:10 dev  
drwxr-xr-x 66 root  
root 8192 Jul 13 07:47  
etc  
drwxr-xr-x 10 root  
root 4096 Jul 5  
14:55 home  
drwxr-xr-x 2 root  
root 4096 Jan 24  
2003 initrd  
drwxr-xr-x 14 root  
root 4096 Jun 9  
00:51 lib  
drwx—— 2 root  
root 4096 Apr 20  
2004 lost+found  
drwxr-xr-x 2 root  
root 4096 Sep  
8 2003 misc  
drwxr-xr-x 3 root  
root 4096 Jun  
1 2004 mnt  
drwxr-xr-x 2 root  
root 4096 Jan 24  
2003 opt  
dr-xr-xr-x 218 root  
root  
0 Jul 6 18:09 proc  
drwxr-x— 18 root  
root 4096 Jul 13 11:28  
root  
drwxr-xr-x 2 root  
root 8192 Jul 3  
23:28 sbin  
drwxrwxrwt 10 root root 31744 Jul 13 17:45 tmp  
drwxr-xr-x 17 root  
root 4096 Jun  
1 2004 usr  
drwxr-xr-x 23 root  
root 4096 Jul 12 16:55  
var

That’s better! Let’s take a minute to explain these columns.  
drwxr-xr-x = file/directory permissions  
20 = link count  
root = owner  
root = group  
4096 = size (in bytes)  
Jul 13 07:47 = last modified time

Want more? This is my personal favorite. Color outpurt, with human readable file sizes.  
**root@hostname &gt; ls -alhF –color=tty**  
total 290K  
drwxr-xr-x 20 root root 4.0K Jul 13 07:47 ./  
drwxr-xr-x 20 root  
root 4.0K Jul 13 07:47  
../  
-rw——- 1 root  
root 18K Jul 14  
05:05 aquota.user  
-rw-r–r– 1 root  
root  
0 Jul 6 18:09 .autofsck  
drwxr-xr-x 8 root  
root 4.0K May 23 12:51  
backupz/  
drwxr-xr-x 2 root  
root 4.0K Jun 15 23:03  
bin/  
drwxr-xr-x 4 root  
root 2.0K Jul 3  
23:49 boot/  
drwxr-xr-x 22 root  
root 116K Jul 6  
18:10 dev/  
drwxr-xr-x 66 root  
root 8.0K Jul 14 00:13  
etc/  
drwxr-xr-x 10 root  
root 4.0K Jul 5  
14:55 home/  
drwxr-xr-x 2 root  
root 4.0K Jan 24  
2003 initrd/  
drwxr-xr-x 14 root  
root 4.0K Jun 9  
00:51 lib/  
drwx—— 2 root  
root 4.0K Apr 20  
2004 lost+found/  
drwxr-xr-x 2 root  
root 4.0K Sep  
8 2003 misc/  
drwxr-xr-x 3 root  
root 4.0K Jun  
1 2004 mnt/  
drwxr-xr-x 2 root  
root 4.0K Jan 24  
2003 opt/  
dr-xr-xr-x 201 root  
root  
0 Jul 6 18:09 proc/  
drwxr-x— 18 root  
root 4.0K Jul 13 11:28  
root/  
drwxr-xr-x 2 root  
root 8.0K Jul 3  
23:28 sbin/  
drwxrwxrwt 10 root  
root 31K Jul 14  
07:39 tmp/  
drwxr-xr-x 17 root  
root 4.0K Jun  
1 2004 usr/  
drwxr-xr-x 23 root  
root 4.0K Jul 12 16:55  
var/

That barely scratches the surface on **ls**. Check the man page for the number of other options.

## cd &amp; pwd

**cd** is another highly used command, yet very basic in it’s  
nature. It simply changes your working directory. By default, with no  
arguments **cd** will work as a shortcut back to your home directory. **pwd** simply prints the working directory. Examples:  
**root@hostname &gt; cd**  
**root@hostname &gt; pwd**  
/root  
**root@hostname &gt; cd /**

**root@hostname &gt; pwd**

/

Other shortcuts exist as well.   
Go “up” one directory:  
**root@hostname &gt; cd ..**

Shortcut to a user’s home directory:  
**root@hostname &gt; cd ~username**

## mkdir &amp; touch

**mkdir** does exactly what it says, it simply makes a directory. Basic usage would be **mkdir** .  
This would create the directoryname within your current working  
directory. Give the directoryname a path, and it will create it there. **touch**  
is similar to mkdir, in that it can create a file if one doesn’t exist.  
This however, is not it’s main purpose. It is able to modify file  
time/date, without modifying the contents. Examples:

**root@hostname &gt; pwd** /root  
root@hostname &gt; mkdir test root@hostname &gt; cd test root@hostname &gt; pwd** /root/test  
**root@hostname &gt; touch testfile root@hostname &gt; ls -lah** total 8  
drwxr-xr-x 2 root  
root 4096 Jul 14 08:01  
./  
drwxr-x— 19 root  
root 4096 Jul 14 08:00  
../  
-rw-r–r– 1 root  
root  
0 Jul 14 08:01 testfile  
**root@hostname &gt; touch testfile** total 8  
drwxr-xr-x 2 root  
root 4096 Jul 14 08:01  
./  
drwxr-x— 19 root  
root 4096 Jul 14 08:00  
../  
-rw-r–r– 1 root  
root  
0 Jul 14 08:02 testfile

Time saving trick for **mkdir**. Use the **-p** option to create parent directories if they don’t exist:  
**root@hostname &gt; mkdir test/test/test** mkdir: cannot create directory `test/test/test’: No such file or directory  
**root@hostname &gt; mkdir -p test/test/test**

## cat, head, more, less, &amp; tail

These are all commands to read the output (or sometimes input) of files. However each has it’s own unique abilities. **cat**  
used with no arguments will simply spew out the content of a file. Give  
it 2 or more files and an output redirection command, and it will (con**cat**enate) the files together. **head** reads only from the beginning of a file. Given no arguments, it will just give you the first 10 lines of a file. **more**  
is a very simple “pager”, It will simple output a file one page at a  
time, so that it’s easy to read through on a console. It is very  
outdated, and lacks a lot of feautres, most improtantly the ability to  
move backwards in a file. **less** is also a “pager”, but it has a bit more features, making it easier to get around a file. It;s commands are based on both **more** and **vi**. It is important to be aware of both though, just in case you come across a system with only one of them. **tail**, is the opposite of **head**. It simply outputes from the end of the file. Examples:  
**root@hostname &gt; ls -lah**  
total 24  
drwxr-xr-x 2 root  
root 4096 Jul 14 08:23  
./  
drwxr-x— 19 root  
root 4096 Jul 14 08:00  
../  
-rw-r–r– 1 root  
root  
2 Jul 14 08:24 1  
-rw-r–r– 1 root  
root  
2 Jul 14 08:23 2  
-rw-r–r– 1 root  
root  
2 Jul 14 08:23 3  
  
  
root@hostname &gt; cat 1**  
a  
**root@hostname &gt; cat 2**  
b  
**root@hostname &gt; cat 3**  
c  
**root@hostname &gt; cat 1 2 3 &gt; all root@hostname &gt; cat all** a  
b  
c

## vi

Love it or hate it, **vi** is the most popular file editor on any \*nix platform. You may have a preference of another editor such as **emacs**, **joe**, or **pico**, but they are not guaranteed to be on every server. **vi** should be in it’s minimal form at least. **vi**  
is actually quite easy to use. Although it has hundres of commands, you  
really only need to know a few to get the job done. I’ve been using it  
for at least 6 years now, and I still only know about 20 commands, even  
though I bought a book full of them! The basics are:  
**root@hostname &gt; vi** **filename** = to start editing a file

### Navigations

The arrows will work most of the time, however on some systems they  
will not work right, so you need to know the shortcuts, or you will  
trash the file.  
**j** = move down one line  
**k** = move up one line  
**h** = move back one character  
**l** or **SPACE** = move forward one character

### Edit mode

All commands are terminated by hitting the **Esc** key. Be careful using the backspace key, as some systems dont recognize it, and it will trash your file.  
**a** = append after cursor  
**i** = insert before cursor  
**o** = a new line below the cursor  
**dd** = delete current line  
**yy** = yank current line  
**p** = inserts the deleted or yanked line below the cursor

### Saving &amp; quitting

**ZZ** = save &amp; quit  
**:q!** = exits edit and quit’s without saving  
**:wq!** = exits edit session, save &amp; quit

## grep

**grep** searches a file or files for a specific pattern. It is a  
very useful command when trying to locate content of a file, without  
having to open a file, or even know which file it’s in for that matter.  
basic use is **grep searchstring filename** Here’s a couple basic xamples, we’ll use it more later in combination with other commands:  
**root@hostname &gt; grep psa /etc/group** psaadm:x:2521:psaadm  
psaftp:x:2522:psaftp  
psaserv:x:2523:apache,psaftp,psaadm  
psacln:x:10001:

How about the same thing, but exclude psaadm:  
**root@hostname &gt; grep psa /etc/group | grep -v psaadm** psaftp:x:2522:psaftp  
psacln:x:10001: