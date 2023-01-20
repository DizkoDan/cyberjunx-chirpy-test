---
id: 194
title: 'Simple remote backups with rsync'
date: '2007-08-26T00:36:15-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/howtos/simple-remote-backups-with-rsync/'
---

A simple way to **securely** mirror your data to a remote server. This tutorial requires [Passwordless SSH](http://www.cyberjunx.com/blog/archives/2007/08/26/passwordless-ssh/) in order for it to work without user intervention (ie, cronjob). Please read my [Passwordless SSH tutorial](http://www.cyberjunx.com/blog/archives/2007/08/26/passwordless-ssh/) before proceeding.

One of the questions I am frequently asked, is *What is the best way to backup my server data?* As any good sysadmin will tell you, the answer is *backup to as many different medium that you can!* A  
lot of people new to systems administration make the fatal mistake of  
believing that any one backup method alone will be good enough. In  
time, we all learn that sooner or later, a failure is going to occur  
with that single backup solution. Then what do you do? You will  
probably start looking for a new job!

Enter [rsync](http://samba.anu.edu.au/rsync/ "rsync").  
Rsync is a great utility for performing full or incremental backups.  
One simple command can copy a single file, or and entire file system to  
wherever you want. But that’s not all! Not only does it copy the data  
to a new location, but it also compares the files to see if anything  
has changed. This results in saved space, and bandwidth (if mirroring  
to a remote system).

The first thing we need to do is make sure that rsync is installed on  
the client machine. The client is the system we are backing up. We will  
refer to these systems in this tutorial as client &amp; server, for  
easier understanding. This does not mean that they can’t both be  
servers. On an RPM based system such as RedHat, Fedora, CentOS, or SuSE, simply query the RPM database: r**pm -qa | grep rsync**  
If it returns a result, you’re ready to go. if not, you need to  
download and install the rsync package for your distribution of linux.

Next, we need to locate the rsync binary. In most cases it will be in  
your path already, but when scheduling jobs, or writing scripts, I  
usually put the full path to binaries just to be safe. Type **which rsync** and it should return something like **/usr/bin/rsync**  
if it doesn’t find it, and you made sure that the package was  
installed, then it is not in your path. You will need to search for  
this using either **locate** or **find**.

It is important to remember that **trailing slashes do matter!**  
Unlike the cp command, rsync uses trailing slashes to decide how data  
is mirrored. A trailing slash on the source directory means that you  
will copy only the files within the source directory. For example let’s  
say you have a directory called /stuff which contains 2 files file1  
&amp; file2:

**rsync -avz /stuff/ -e ssh username@server:/backup/dir/**  
Will produce **/backup/dir/file1 &amp; /backup/dir/file2**

Now take the same command, and remove that trailing slash on /stuff:  
**rsync -avz /stuff -e ssh username@server:/backup/dir/** Will produce **/backup/dir/stuff/file1&amp; /backup/dir/stuff/file2**

Now for the actual commands! Rsync has many options, and I strongly suggest you read the man page (**man rsync**) to learn more. For this tutorial, we will use **-a**, **-v**, **-z**,**–delete**, **-exclude**, &amp; **-e**.   
 **-a** = Archive mode. It is equal to using -rlptgoD (**man rsync**)  
 **-v** = Verbose  
 **-z** = Compression. This compresses all data before sending it using the same compression method as gzip.  
 **–delete** = Delete files on the server that don’t exist on the client  
**-exclude** = Exactly what is says. Excludes a file or pattern  
 **-e** = Choose remote shell. We use this to specify SSH

Backup the entire server (deleting missing files, and excluding the proc filesystem):  
**rsync -avz –delete –exclude=/proc / -e ssh username@server:/backup/dir/**

Backup a single folder/filesystem (deleting missing files):  
**rsync -avz –delete /etc -e ssh username@server:/backup/dir/**

Making sense? Good! Now lets automate this sucker.   
**crontab -e  
07 03 \* \* \* /usr/bin/rsync -avz –delete /etc -e ssh username@server:/backup/dir/ &gt; /dev/null 2&gt;&amp;1**

Setting up cron is beyond the scope of this tutorial, but a quick rundown of this is:  
Mirror /etc to our remote server in /backup/dir/ every night at 3:07am.

Once you get the basics down, It’s easy to make a solid backup  
solution. I like to rsync to a 2nd hard drive on my system, then rsync  
that to a remote server. This gives me an extra level of protection, in  
case my server blows up, or one of the bad guys get in and wipe out my  
data. Another cool thing to do, is use hard links (**man ln**) with  
rsync, then setup a rotation schedule say daily for a week. This gives  
you 7 full backups, but only uses the space of 1 full backup plus  
whatever incremental changes happen over the week. The advantage versus  
normal incremental backups, is that it appears as a full backup  
everyday. So if you need to restore from say Friday, you don’t have to  
restore Sunday first. Just copy the Friday backup.