---
id: 839
title: 'Sync Files and Folders Outside Your My Dropbox Folder'
date: '2009-02-16T20:00:00-04:00'
author: DizkoDan
excerpt: ' <p><img src="http://cache.gawker.com/assets/images/lifehacker/2009/02/dbo.png" width="351" height="198" />The popular cross-platform file-syncing application <a href="https://www.getdropbox.com/">Dropbox</a> is a <a href="http://lifehacker.com/398696/five-best-file-syncing-tools">hit among Lifehacker readers</a>, but it has one major drawback: It only syncs files placed inside the My Dropbox folder. Here''s how to get around that limitation.</p> <p>In order to sync files and folders that live outside the My Dropbox folder, you need to create a symbolic link between the My Dropbox folder and the folder on your drive that you want to sync. Symbolic links are sort of like shortcuts, so if you had a folder called SyncMe that lived on your desktop, you''d create a symbolic link that made it appear as though SyncMe also lived inside the My Dropbox folder. This process varies depending on your operating system. On Windows:</p> <blockquote><p>Use either the <strong><a href="http://www.microsoft.com/technet/sysinternals/FileAndDisk/junction.mspx">JUNCTION</a></strong> utility from Sysinternals, or the <strong>MKLINK</strong> command built in to Windows Vista and Server 2008, for example:</p> <p><tt>&nbsp;junction&nbsp;"C:\Documents&nbsp;and&nbsp;Settings\User\My&nbsp;Documents\My&nbsp;Dropbox\DesiredFolder"&nbsp;"C:\Path\To\DesiredFolder"</tt><br /> <tt>&nbsp;mklink&nbsp;/D&nbsp;"C:\Users\Steve\Documents\Dropbox\DesiredFolder"&nbsp;"C:\Path\To\DesiredFolder"</tt> </p> <p>Or, if you prefer a GUI, install <a href="http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html">Link Shell Extension</a>.</p> <p>[You could also] use <strong><a href="http://www.microsoft.com/downloads/details.aspx?FamilyID=c26efa36-98e0-4ee9-a7c5-98d0592d8c52&amp;DisplayLang=en">SyncToy</a></strong> to echo changes from another folder to your Dropbox folder. This keeps 2 copies on disk though.</p></blockquote> <p>On OS X or Linux, try the following:</p> <blockquote><p>Use the <strong>ln</strong> command, for example: </p> <p><tt>&nbsp;ln&nbsp;-s&nbsp;/path/to/desired-folder&nbsp;~/Dropbox/desired-folder&nbsp;</tt> </p> <p>This works with files too: </p> <p><tt>&nbsp;ln&nbsp;-s&nbsp;/path/to/desired-file&nbsp;~/Dropbox/desired-file&nbsp;</tt> </p> <p>Another easy way to do this with Terminal is type the <tt>ln&nbsp;-s</tt> part, then from Finder drag the folder/file that you want into the Terminal window then drag the Dropbox folder and hit return. </p> <p>Note that an Alias file or folder does not work.</p></blockquote> <p>The wiki also offers an Automator workflow to streamline the process if you''re using OS X. If this syncing obstacle has held you back from using Dropbox, give these symbolic links a try. If this seems like too much of a hassle, <a href="http://lifehacker.com/5143261/syncplicity-for-mac-windows-open-to-all">previously mentioned Syncplicity</a> and a few <a href="http://lifehacker.com/398696/five-best-file-syncing-tools">other popular file-syncing apps</a> have user-defined sync folders baked in.</p> <div class="related"><a href="http://wiki.getdropbox.com/TipsAndTricks/SyncOtherFolders">How to sync folders (or files) that exist outside the "My Dropbox" folder</a> [Dropbox Wiki via <a href="http://ask.metafilter.com/114339/Files-on-BOTH-Computer-and-Dropbox-Online-Storage">Ask MetaFilter</a>]</div> '
layout: post
guid: Lifehacker-5154698
permalink: /2009/02/16/sync-files-and-folders-outside-your-my-dropbox-folder/
aktt_notify_twitter:
    - 'no'
tags:
    - 'get stuff done'
    - Lifehacker
    - 'tech tips'
---

![](http://cache.gawker.com/assets/images/lifehacker/2009/02/dbo.png)The popular cross-platform file-syncing application [Dropbox](https://www.getdropbox.com/) is a [hit among Lifehacker readers](http://lifehacker.com/398696/five-best-file-syncing-tools), but it has one major drawback: It only syncs files placed inside the My Dropbox folder. Here’s how to get around that limitation.

In order to sync files and folders that live outside the My Dropbox folder, you need to create a symbolic link between the My Dropbox folder and the folder on your drive that you want to sync. Symbolic links are sort of like shortcuts, so if you had a folder called SyncMe that lived on your desktop, you’d create a symbolic link that made it appear as though SyncMe also lived inside the My Dropbox folder. This process varies depending on your operating system. On Windows:

> Use either the **[JUNCTION](http://www.microsoft.com/technet/sysinternals/FileAndDisk/junction.mspx)** utility from Sysinternals, or the **MKLINK** command built in to Windows Vista and Server 2008, for example:
> 
> <tt> junction "C:\\Documents and Settings\\User\\My Documents\\My Dropbox\\DesiredFolder" "C:\\Path\\To\\DesiredFolder"</tt>  
> <tt> mklink /D "C:\\Users\\Steve\\Documents\\Dropbox\\DesiredFolder" "C:\\Path\\To\\DesiredFolder"</tt>
> 
> Or, if you prefer a GUI, install [Link Shell Extension](http://schinagl.priv.at/nt/hardlinkshellext/hardlinkshellext.html).
> 
> \[You could also\] use **[SyncToy](http://www.microsoft.com/downloads/details.aspx?FamilyID=c26efa36-98e0-4ee9-a7c5-98d0592d8c52&DisplayLang=en)** to echo changes from another folder to your Dropbox folder. This keeps 2 copies on disk though.

On OS X or Linux, try the following:

> Use the **ln** command, for example:
> 
> <tt> ln -s /path/to/desired-folder ~/Dropbox/desired-folder </tt>
> 
> This works with files too:
> 
> <tt> ln -s /path/to/desired-file ~/Dropbox/desired-file </tt>
> 
> Another easy way to do this with Terminal is type the <tt>ln -s</tt> part, then from Finder drag the folder/file that you want into the Terminal window then drag the Dropbox folder and hit return.
> 
> Note that an Alias file or folder does not work.

The wiki also offers an Automator workflow to streamline the process if you’re using OS X. If this syncing obstacle has held you back from using Dropbox, give these symbolic links a try. If this seems like too much of a hassle, [previously mentioned Syncplicity](http://lifehacker.com/5143261/syncplicity-for-mac-windows-open-to-all) and a few [other popular file-syncing apps](http://lifehacker.com/398696/five-best-file-syncing-tools) have user-defined sync folders baked in.

<div class="related">[How to sync folders (or files) that exist outside the “My Dropbox” folder](http://wiki.getdropbox.com/TipsAndTricks/SyncOtherFolders) [Dropbox Wiki via [Ask MetaFilter](http://ask.metafilter.com/114339/Files-on-BOTH-Computer-and-Dropbox-Online-Storage)]</div>