---
id: 849
title: 'Todo.txt CLI Manages Your Tasks from the Command Line'
date: '2009-02-18T13:00:13-04:00'
author: DizkoDan
excerpt: ' <p><img src="http://cache.gawker.com/assets/images/lifehacker/2009/02/todotxt20-header.png" width="504" height="260" style="display:block;" /> Dozens of fancy point-and-click task managers promise to organize your to-do list, but so often power users find that nothing outdoes that trusty old classic: the <code>todo.txt</code> file.</p> <p>If you''re a <a class="autolink" title="Click here to read more posts tagged COMMAND LINE" href="http://lifehacker.com/tag/command-line/">command line</a> lover who skips checkboxes and drop-downs to dash off notes and tasks in a regular old text file, or you''re intrigued by the idea and <em>wish</em> your todo.txt chops were stronger, read on.</p> <p><br /> <br /> I''ve been a heavy <code>todo.txt</code> user for years. Back in 2006, I started <a href="http://lifehacker.com/183429/todotxt-in-action">developing a command line interface (CLI) to my todo.txt</a> which lets me add to and check off items without launching a full-on text editor. Three years of daily (or at least weekly) use later, version 2.0 of the script is now available. It offers basic to advanced commands for managing your <code>todo.txt</code> and other text files you might use to capture information, like <code>ideas.txt</code> or <code>maybelater.txt</code>. Let''s take a look.</p> <p><b>Who This Is Meant For</b>: If you''re comfortable working in the terminal, changing permissions on a file, and working with Unix-style text commands, then the <code>todo.txt</code> CLI is for you. If you don''t spend a good amount of time at the command line&mdash;either in the Terminal on your Mac, or using a Unix command line or emulator on Windows&mdash;you''re going to think this whole thing is arcane and confusing. (In that case, we highly recommend <a href="http://lifehacker.com/software/geek-to-live/get-organized-with-remember-the-milk-309789.php">getting organized with Remember the Milk</a>. If you want to boost your command line chops on Windows, check out our <a href="http://lifehacker.com/software/top/geek-to-live--introduction-to-cygwin-part-i-179514.php">introduction to Cygwin</a>.)</p> <p>You''ve already got CLI religion? Good. Let''s get started on some hot <code>todo.txt</code> command line action.</p> <p><a href="http://todotxt.com/library/todo.sh/todo.txt-cli-2.0.zip"><img src="http://cache.lifehacker.com/assets/resources/2007/05/dl-icon.png"/></a> <b>Quick Start Guide:</b></p> <ol> <li><a href="http://todotxt.com/library/todo.sh/todo.txt-cli-2.0.zip">Download the Todo.txt CLI 2.0 zip file</a> and extract it. You''ll get two files. Place both <code>todo.cfg</code> (the configuration file) and <code>todo.sh</code> in your home directory.</li> <li>Open the <code>todo.cfg file</code> with your text editor of choice. Set the TODO_DIR variable to the right path for your setup. For example, on my Windows PC, this line reads:<br /> <code>TODO_DIR="C:/Documents and Settings/gina/My Documents"</code><br /> On my Mac, this line reads:<br /> <code>TODO_DIR="/Users/gina/Documents/todo"</code></li> <li>Make the <code>todo.sh</code> file executable by using the command: <code>chmod +x todo.sh</code></li> <li>(OPTIONAL) Alias the letter t to <code>todo.sh</code> to save keystrokes while you use it. In your <code>~/.bash_profile</code> file, add the line:<br /> <code>alias t=''~/todo.sh''</code></li> </ol> <p>Now you''re ready to put this script to work!</p> <h3>Basic Usage</h3> <p>Before we start, keep in mind that this CLI isn''t trying to reinvent the text editor. If you want to do big bulk edits to a lot of items in your <code>todo.txt</code>, just open it up in your favorite text editor to do so. But for quick, one-hit access to add items, mark items as complete, or slice and dice your list by project or priority, <code>todo.sh</code> is for you.</p> <p>For example, to add a line to your <code>todo.txt</code> file, at the command line, type:</p> <blockquote> <p><code>$ t add "Pick up milk"</code></p> </blockquote> <p>Add a few more items for good measure:</p> <blockquote> <p><code>$ t add "Pick up the dry cleaning"</code><br /> <code>$ t add "Clean out the inbox"</code></p> </blockquote> <p>Now, to see all the items on your list, use:</p> <blockquote> <p><code>$ t ls</code></p> </blockquote> <p>The output will look like this:</p> <blockquote> <p><code>$ t ls<br /> 03 Clean out the inbox<br /> 01 Pick up milk<br /> 02 Pick up the dry cleaning<br /> --<br /> TODO: 3 tasks in C:/Documents and Settings/gina/My Documents/todo.txt.</code></p> </blockquote> <p>Now, you can reference each item by its ID&mdash;which is actually the line number it lives at in the <code>todo.txt</code> file. For instance, to prioritize task 1 to the highest level&mdash;priority A&mdash;use this command:</p> <blockquote> <p><code>$ t pri 1 A</code></p> </blockquote> <p>To mark task 2 as complete, use <code>todo.sh</code>''s do action:</p> <blockquote> <p><code>$ t do 2</code></p> </blockquote> <p>Since a video is worth a million words, see this in action in this screencast demonstration of a to-do list you might find for a crew member on Battlestar Galactica. (Go full-screen to see what''s being typed more clearly.)</p> <p>  <img src="http://cache.gawker.com/assets/images/lifehacker/2009/02/3263629.jpg" style="display: none;" class="embeddedVideoThumbnail"/> If this video clip isn''t clear enough for you, try this <a href="http://todotxt.com/library/todo.sh/screencast/">alternate high-res location</a>.</p> <p><br /></p> <h3>Advanced Usage</h3> <p>Once you''ve got the basics of working with your <code>todo.txt</code> down, it''s time to dive into more advanced tricks. Here are a few more things this CLI can do.</p> <ul> <li><b>Replace or delete a task; append or prepend text to a line.</b> When you want to re-word a task or add a context, project, or additional info to it, use the replace, append, and prepend actions to do so. For example, add "ready at 3PM" to your "Pick up the dry cleaning task" with this command:<br /> <blockquote><code>$ t append 2 "ready at 3PM"</code></blockquote> </li> <li><b>See all the contexts and projects in your list.</b> If you''re using the + and @ sign format to signify projects and contexts, use the listcon and listproj (or lsc and lsprj for short) commands to see a short list of all your contexts or projects in your <code>todo.txt</code>.</li> <li><b>Move items from your todo.txt to another text file.</b> Say you''ve decided that the "Learn how to speak French" task is actually something you''re not quite committed to doing&mdash;yet. Use <code>todo.sh</code>''s mv command to zip that task from <code>todo.txt</code> to another text file in your todo directory. For example, this command will move it into a <code>maybelater.txt</code> file:<br /> <blockquote><code>$ t move 10 maybelater.txt</code></blockquote> </li> <li><b>List the contents of another text file.</b> Since I got so used to working with <code>todo.txt</code> this way, there''s now support for working with other text files. For example, you can list the contents of your <code>maybelater.txt</code> file using the command:<br /> <blockquote><code>$ t listfile maybelater.txt</code></blockquote> <p>Likewise, you can add a line to another file using:<br /></p> <blockquote><code>$ t addto ideas.txt "My bright idea"</code></blockquote> <p>You can also search the contents of another text file by adding a keyword after the list command, ala:<br /></p> <blockquote><code>$ t lf ideas.txt apple</code></blockquote> </li> </ul> <p>See all the options available to you using the <code>todo.sh -h</code> command. The <a href="http://todotxt.com/library/todo.sh/usage.txt">full usage manual is available here</a>.</p> <h3>Further Info and Related Projects</h3> <p>The <code>todo.txt</code> CLI has lived over at its official homepage, <a href="http://todotxt.com">Todotxt.com</a>, for years now, and although I haven''t posted an update there since 2006, an <a href="http://tech.groups.yahoo.com/group/todotxt/">active mailing list of over 500 members</a> is still going strong. Since this project is open source, happily several other <code>todo.txt</code> projects have sprung up over the years, including <a href="http://www.beckingham.net/task.html">Task</a>, which offers even more features than my little script does.</p> <p>If you''re a programmer who wants to add to this script or a user with questions or ideas about the <code>todo.txt</code> CLI, either post them here or consider <a href="http://tech.groups.yahoo.com/group/todotxt/">joining the mailing list</a> for support. For a full history of this script''s development&mdash;including its three-year hiatus&mdash;see <a href="http://todotxt.com/library/todo.sh/changelog.txt">its full changelog</a>.</p> <p>Think using a command line interface to a text file is insane or fantastic (or both)? Tried out <code>todo.txt</code>? Tell us what you think in the comments.</p> <p><i><strong><a href="http://ginatrapani.org">Gina Trapani</a></strong>, Lifehacker''s founding editor, is still married to her todo.txt file even after a sordid affair with Remember the Milk. Her weekly feature, <a href="http://lifehacker.com/tag/smarterware/">Smarterware</a>, appears every Wednesday on Lifehacker. Subscribe to the <a href="http://lifehacker.com/tag/smarterware/index.xml">Smarterware tag feed</a> to get new installments in your newsreader.</i></p> '
layout: post
guid: Lifehacker-5155450
permalink: /2009/02/18/todotxt-cli-manages-your-tasks-from-the-command-line/
aktt_notify_twitter:
    - 'no'
tags:
    - 'get stuff done'
    - Lifehacker
    - 'tech tips'
---

![](http://cache.gawker.com/assets/images/lifehacker/2009/02/todotxt20-header.png) Dozens of fancy point-and-click task managers promise to organize your to-do list, but so often power users find that nothing outdoes that trusty old classic: the `todo.txt` file.

If you’re a [command line](http://lifehacker.com/tag/command-line/ "Click here to read more posts tagged COMMAND LINE") lover who skips checkboxes and drop-downs to dash off notes and tasks in a regular old text file, or you’re intrigued by the idea and *wish* your todo.txt chops were stronger, read on.

  
  
 I’ve been a heavy `todo.txt` user for years. Back in 2006, I started [developing a command line interface (CLI) to my todo.txt](http://lifehacker.com/183429/todotxt-in-action) which lets me add to and check off items without launching a full-on text editor. Three years of daily (or at least weekly) use later, version 2.0 of the script is now available. It offers basic to advanced commands for managing your `todo.txt` and other text files you might use to capture information, like `ideas.txt` or `maybelater.txt`. Let’s take a look.

**Who This Is Meant For**: If you’re comfortable working in the terminal, changing permissions on a file, and working with Unix-style text commands, then the `todo.txt` CLI is for you. If you don’t spend a good amount of time at the command line—either in the Terminal on your Mac, or using a Unix command line or emulator on Windows—you’re going to think this whole thing is arcane and confusing. (In that case, we highly recommend [getting organized with Remember the Milk](http://lifehacker.com/software/geek-to-live/get-organized-with-remember-the-milk-309789.php). If you want to boost your command line chops on Windows, check out our [introduction to Cygwin](http://lifehacker.com/software/top/geek-to-live--introduction-to-cygwin-part-i-179514.php).)

You’ve already got CLI religion? Good. Let’s get started on some hot `todo.txt` command line action.

[![](http://cache.lifehacker.com/assets/resources/2007/05/dl-icon.png)](http://todotxt.com/library/todo.sh/todo.txt-cli-2.0.zip) **Quick Start Guide:**

1. [Download the Todo.txt CLI 2.0 zip file](http://todotxt.com/library/todo.sh/todo.txt-cli-2.0.zip) and extract it. You’ll get two files. Place both `todo.cfg` (the configuration file) and `todo.sh` in your home directory.
2. Open the `todo.cfg file` with your text editor of choice. Set the TODO\_DIR variable to the right path for your setup. For example, on my Windows PC, this line reads:  
    `TODO_DIR="C:/Documents and Settings/gina/My Documents"`  
     On my Mac, this line reads:  
    `TODO_DIR="/Users/gina/Documents/todo"`
3. Make the `todo.sh` file executable by using the command: `chmod +x todo.sh`
4. (OPTIONAL) Alias the letter t to `todo.sh` to save keystrokes while you use it. In your `~/.bash_profile` file, add the line:  
    `alias t='~/todo.sh'`

Now you’re ready to put this script to work!

### Basic Usage

Before we start, keep in mind that this CLI isn’t trying to reinvent the text editor. If you want to do big bulk edits to a lot of items in your `todo.txt`, just open it up in your favorite text editor to do so. But for quick, one-hit access to add items, mark items as complete, or slice and dice your list by project or priority, `todo.sh` is for you.

For example, to add a line to your `todo.txt` file, at the command line, type:

> `$ t add "Pick up milk"`

Add a few more items for good measure:

> `$ t add "Pick up the dry cleaning"`  
> `$ t add "Clean out the inbox"`

Now, to see all the items on your list, use:

> `$ t ls`

The output will look like this:

> `$ t ls<br></br> 03 Clean out the inbox<br></br> 01 Pick up milk<br></br> 02 Pick up the dry cleaning<br></br> --<br></br> TODO: 3 tasks in C:/Documents and Settings/gina/My Documents/todo.txt.`

Now, you can reference each item by its ID—which is actually the line number it lives at in the `todo.txt` file. For instance, to prioritize task 1 to the highest level—priority A—use this command:

> `$ t pri 1 A`

To mark task 2 as complete, use `todo.sh`‘s do action:

> `$ t do 2`

Since a video is worth a million words, see this in action in this screencast demonstration of a to-do list you might find for a crew member on Battlestar Galactica. (Go full-screen to see what’s being typed more clearly.)

<object class="left gawkerVideo embeddedVideo" height="380" width="506"><param name="movie" value="http://vimeo.com/moogaloop.swf?clip_id=3263629&server=vimeo.com&show_title=1&show_byline=1&show_portrait=0&color=&fullscreen=1"></param><param name="allowFullScreen" value="true"></param></object>![](http://cache.gawker.com/assets/images/lifehacker/2009/02/3263629.jpg) If this video clip isn’t clear enough for you, try this [alternate high-res location](http://todotxt.com/library/todo.sh/screencast/).

### Advanced Usage

Once you’ve got the basics of working with your `todo.txt` down, it’s time to dive into more advanced tricks. Here are a few more things this CLI can do.

- **Replace or delete a task; append or prepend text to a line.** When you want to re-word a task or add a context, project, or additional info to it, use the replace, append, and prepend actions to do so. For example, add “ready at 3PM” to your “Pick up the dry cleaning task” with this command:  
      
    > `$ t append 2 "ready at 3PM"`
- **See all the contexts and projects in your list.** If you’re using the + and @ sign format to signify projects and contexts, use the listcon and listproj (or lsc and lsprj for short) commands to see a short list of all your contexts or projects in your `todo.txt`.
- **Move items from your todo.txt to another text file.** Say you’ve decided that the “Learn how to speak French” task is actually something you’re not quite committed to doing—yet. Use `todo.sh`‘s mv command to zip that task from `todo.txt` to another text file in your todo directory. For example, this command will move it into a `maybelater.txt` file:  
      
    > `$ t move 10 maybelater.txt`
- **List the contents of another text file.** Since I got so used to working with `todo.txt` this way, there’s now support for working with other text files. For example, you can list the contents of your `maybelater.txt` file using the command:  
      
    > `$ t listfile maybelater.txt`
    
    Likewise, you can add a line to another file using:
    
    > `$ t addto ideas.txt "My bright idea"`
    
    You can also search the contents of another text file by adding a keyword after the list command, ala:
    
    > `$ t lf ideas.txt apple`

See all the options available to you using the `todo.sh -h` command. The [full usage manual is available here](http://todotxt.com/library/todo.sh/usage.txt).

### Further Info and Related Projects

The `todo.txt` CLI has lived over at its official homepage, [Todotxt.com](http://todotxt.com), for years now, and although I haven’t posted an update there since 2006, an [active mailing list of over 500 members](http://tech.groups.yahoo.com/group/todotxt/) is still going strong. Since this project is open source, happily several other `todo.txt` projects have sprung up over the years, including [Task](http://www.beckingham.net/task.html), which offers even more features than my little script does.

If you’re a programmer who wants to add to this script or a user with questions or ideas about the `todo.txt` CLI, either post them here or consider [joining the mailing list](http://tech.groups.yahoo.com/group/todotxt/) for support. For a full history of this script’s development—including its three-year hiatus—see [its full changelog](http://todotxt.com/library/todo.sh/changelog.txt).

Think using a command line interface to a text file is insane or fantastic (or both)? Tried out `todo.txt`? Tell us what you think in the comments.

***[Gina Trapani](http://ginatrapani.org)**, Lifehacker’s founding editor, is still married to her todo.txt file even after a sordid affair with Remember the Milk. Her weekly feature, [Smarterware](http://lifehacker.com/tag/smarterware/), appears every Wednesday on Lifehacker. Subscribe to the [Smarterware tag feed](http://lifehacker.com/tag/smarterware/index.xml) to get new installments in your newsreader.*