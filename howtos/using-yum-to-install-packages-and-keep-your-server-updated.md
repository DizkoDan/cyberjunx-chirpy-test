---
id: 196
title: 'Using yum to install packages, and keep your server updated.'
date: '2007-08-26T00:43:15-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/howtos/using-yum-to-install-packages-and-keep-your-server-updated/'
---

One of the biggest complaints users of RPM based Linux distros have  
always had, is the package management. RPM’s are great, but you often  
find yourself in what we so kindly refer to as “dependency hell”. In  
recent years RedHat implemented their up2date program, which uses their  
RedHat Network to install/update packages. After RedHat 9, RedHat  
decided to split off their Linux Distro into two projects: [RedHat Enterprise](http://www.redhat.com/software/rhel/ "RedHatEnterprise") &amp; [The Fedora Project](http://www.fedoraproject.org "TheFedoraProject"). In doing so, they decided that RHN would become a pay service, only available to Enterprise customers. Fedora decided to use [YUM](http://linux.duke.edu/projects/yum/ "YUM").

## **First, a bit of history.**

YUM stands for: “Yellow dog Updater, Modifed”. If you are not familiar  
with Yellow dog, it is a Linux distribution based on RedHat/Fedora, for  
Apple computers. Originally, they created a package management system  
called YUP (Yellow dog UPdater). It handled basic dependency  
resolution, which made for automation of RPM installation, and  
maintenance. The Duke University Physics department began using it for  
their internal needs. YUP was rather slow, and lacking features, so a  
sysadmin at Duke named [Seth Vidal](http://blog.sethdot.org/index.cgi "SethVidal") began reworking the code. Eventually, he ended up rewriting it complately, so he renamed it YUM.

##  **So what’s so great about YUM?**

Unlike the up2date model, YUM can connect to multiple repositories, and  
is not reliant on a single server side solution. A repository (repo) is  
simply a directory full of RPM’s on a server accessible via ftp, http,  
or even a local filesystem. Each repo has a directory full of headers,  
and a packagelist. A repo can have anything from a small group of custom packages, to  
a full Linux distribution. This makes it a great way to disrtrubute RPM’s.

## **Basic configuration:**

In addition to Fedora, several other Linux distros use YUM as their package managemnt system. most notably, [CentOS](http://www.centos.org "CentOS").  
Since this is a hosting site, I’m going to focus on CentOS rather than  
Fedora. Fedora is considered a development OS, and if you are serious  
about hosting, you should not be using bleeding edge software. CentOS  
is simply RedHat Enterprise stripped of any proprietary code. It gets  
updates within a day or two (usually), or RedHat, and is a great  
alternative if you do not require the support that RedHat provides.

In it’s most basic configuration, YUM will have two repos; **base** &amp; **updates.** These repos are configured in one of two places. Either **/etc/yum.conf,** or **/etc/yum.repos.d/reponame.repo**  
The actual configuration is the same on either, but the yum.repos.d  
method is the new way. Let’s take a look at a couple of examples.

**/etc/yum.conf** on a CentOS 3.4 system:

- - - - - -

\[main\]  
cachedir=/var/cache/yum  
debuglevel=2  
logfile=/var/log/yum.log  
pkgpolicy=newest  
distroverpkg=redhat-release  
installonlypkgs=kernel kernel-smp kernel-hugemem kernel-enterprise  
kernel-debug kernel-unsupported kernel-smp-unsupported  
kernel-hugemem-unsupported  
tolerant=1  
exactarch=1

\[base\]  
name=CentOS-$releasever – Base  
baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/  
gpgcheck=1

\#released updates  
\[update\]  
name=CentOS-$releasever – Updates  
baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/  
gpgcheck=1

- - - - - -

**/etc/yum.conf** on a CentOS 4.1 system:

- - - - - -

\[main\]  
cachedir=/var/cache/yum  
debuglevel=2  
logfile=/var/log/yum.log  
pkgpolicy=newest  
distroverpkg=centos-release  
tolerant=1  
exactarch=1  
retries=20  
obsoletes=1  
gpgcheck=1

\# PUT YOUR REPOS HERE OR IN separate files named file.repo  
\# in /etc/yum.repos.d

- - - - - -

**/etc/yum.repos.d/CentOS-Base.repo**

- - - - - -

\[base\]  
name=CentOS-$releasever – Base  
baseurl=http://mirror.centos.org/centos/$releasever/os/$basearch/  
gpgcheck=1

\#released updates  
\[update\]  
name=CentOS-$releasever – Updates  
baseurl=http://mirror.centos.org/centos/$releasever/updates/$basearch/  
gpgcheck=1

- - - - - -

## What does it all mean?

From the trusty man page (man yum.conf)

## \[main\] options

The \[main\] section must exist for yum to do anything. It  
consists of the following options:

**cachedir**  
directory where yum should store its cache and db files.  
 **debuglevel**  
debug level. practical range is 0-10. default is 2.  
  
**errorlevel**  
debug level. practical range is 0-10. default is 2.  
  
**logfile**  
full directory and file name for where yum should write its log  
file.  
  
**assumeyes**  
1 or 0 – tells yum whether or not to prompt you for  
confirmation of actions. Same as -y on the command line. Default to  
0\.  
  
**tolerant**  
1 or 0 – Tells yum to be tolerant of errors on the command line  
with regard to packages. For example: if you request to install  
foo, bar and baz and baz is installed; yum won’t error out  
complaining that baz is already installed. same as -t on the  
command line. Default to 0(not tolerant)  
  
**pkgpolicy=***\[newest|last\]*  
Default: *newest*. Package sorting order. When a package  
is available from multiple servers, *newest* will install the  
most recent version of the package found. *last* will sort the  
servers alphabetically by **serverid** and install the version  
of the package found on the last server in the resulting list. If  
you don’t understand the above then you’re best left not including  
this option at all and letting the default occur.  
 **exclude**  
list of packages to exclude from updates or installs. This  
should be a space separated list. Filename globs \*,?,., etc are  
allowed  
  
**exactarch**  
1 or 0 – set to 1 to make yum update only update the  
architectures of packages that you have installed. IE: with this  
enabled yum will not install an i686 package to update an i386  
package.  
  
**commands**  
list of functional commands to run if no functional commands  
are specified on the command line. ie: commands = update foo bar  
baz quux none of the short options (-y, -e, -d, etc) will be taken  
in the field.  
  
**distroverpkg**  
package to use to determine the “version” of the distribution –  
can be any package you have installed – defaults to redhat-release.  
  
**diskspacecheck**  
set this to 0 to disable the checking for sufficient diskspace  
before the rpm transaction is run. default is 1 (to perform the  
check)  
 **retries**  
Set the number of times any attempt to retrieve a file should  
retry before returning an error. Setting this to 0 makes it try  
forever. Default to 6.  
  
**kernelpkgnames**  
list of package names that are kernels – this is really only  
here for the kernel updating portion – this should be removed out  
in 2.1 series.  
  
**installonlypkgs**  
list of packages that should only ever be installed, never  
updated – kernels in particular fall into this category. Defaults  
to kernel, kernel-smp, kernel-bigmem, kernel-enterprise,  
kernel-debug, kernel-unsupported.

## \[server\] options

The server section(s) take the following form:

**serverid**  
must be a unique name for each server, one word.  
 **baseurl**  
must be a url to the directory where the yum repository’s  
‘headers’ directory lives. Can be an [http://,](http://,/) ftp:// or file:// url. You can specify  
multiple urls in one baseurl statement. The best way to do this is  
like this:  
\[serverid\]  
name=Some name for this server  
baseurl=<url://server1/path/to/repository/>  
<url://server2/path/to/repository/>  
<url://server3/path/to/repository/>  
If you list more than one baseurl= statement in a repository you  
will find yum will ignore the earlier ones and probably act  
bizarrely. Don’t do this, you’ve been warned.  
 **name** a human readable string describing the repository.  
 **gpgcheck** either ‘1’ or ‘0’. This tells yum whether or not it should  
perform a gpg signature check on the packages gotten from this  
server  
 **failovermethod** can be either ’roundrobin’ or ‘priority’. roundrobin randomly  
selects a url out of the list of urls to start with and proceeds  
through each of them as it encounters a failure contacting the  
host.  
priority starts from the first baseurl listed and reads through  
them sequentially.  
failovermethod defaults to roundrobin if not specified.  
 **exclude** same as the \[main\] exclude but this is only for this server  
variables, listed below, are honored here.

## Now Let’s put this to use:

Let’s say we just installed CentOS 4.1. We want to get our system fully  
updated, since new errata has been released since the CD images were  
created. Since this is (at the time of this writing) a fairly recent  
release, there won’t be too many errata released yet. But on an older  
release, there will be a lot. to update everything, we simply type:  
**yum update**

Now let’s say we wanted to install Apache. Simply type:  
**yum install httpd**

Don’t remember exactly what the package is called? Apache for example is now called httpd. Try searching for it using:  
**yum search apache**

It’s gonna give you a lot of results, but if you dig through it, you’ll find:  
 **httpd.i386**  
2.0.52-12.ent.centos4 installed  
Matched from:  
Apache HTTP Server  
Apache is a powerful, full-featured, efficient, and freely-available  
Web server. Apache is also the most popular Web server on the  
Internet.  
http://httpd.apache.org/

## 3rd Party repositories:

There are tons of 3rd party repos out there. You must be careful from  
which you choose to install packages. Not all “maintainers” adhere to  
standards, so mixing packages from multiple repos could become a  
nightmare. Personally, I stick to the repos under RPMForge:  
[DAG](http://dag.wieers.com/home-made/apt/ "DAG")  
[Dries](http://dries.studentenweb.org/apt/ "Dries")  
[FreshRPMS](http://www.freshrpms.net "FreshRPMS")

Adding repos is as simple as editing your **/etc/yum.conf** or creating a file under **/etc/yum.repos.d/**. We’ll create a repo for Dag as an example.

**/etc/yum.conf** on a CentOS 3.4 system add the following to the bottom of the file:

- - - - - -

\[Dag\]  
name=Dag RPM Repository  
baseurl=http://apt.sw.be/redhat/el3/en/$basearch/dag  
gpgcheck=1

Create a file called **/etc/yum.repos.d/Dag.repo** with the following:

- - - - - -

\[dag\]  
name=Dag RPM Repository for Red Hat Enterprise Linux  
baseurl=http://apt.sw.be/redhat/el$releasever/en/$basearch/dag  
gpgcheck=1  
enabled=1

## Nightly updates:

The YUM RPM comes with an init script to do nightly updates. To enable this, simply type the following:  
**chkconfig yum on**

## Full version upgrades:

It is completely possible to do a full version upgrade (CentOS 3.x –  
CentOS 4.1) via YUM. This is not recommended, as there are often major  
changes between releases, that wont clean up properly. However, it can  
get an old system that you dont have physical access to updated, and if  
you know what you are doing, it’s only a little extra work to get  
things right.

### **I make no guarantees that this will work for you! In  
fact I recommend you not use it, as it could leave your system in an  
unusable state. If you do try this, don’t be a jerk, BACK UP YOUR  
SYSTEM! YOU HAVE BEEN WARNED!**


- **BACKUP YOUR DATA**
- **BACKUP YOUR DATA (No, Seriously!)**
- **Install the new RPM Key**
- <span class="small">rpm –import [RPM-GPG-KEY-CentOS-4](http://mirror.centos.org/centos/RPM-GPG-KEY-CentOS-4 "RPM-GPG-KEY-CentOS-4")</span>
- **Upgrade YUM**
- <span class="small">rpm -Uvh </span>[yum-2.2.1-1.centos4.noarch.rpm](http://mirror.centos.org/centos/4.1/os/i386/CentOS/RPMS/yum-2.2.1-1.centos4.noarch.rpm "yum-2.2.1-1.centos4.noarch.rpm")
- **Upgrade the centos-release package**
- <span class="small">rpm -Uvh [centos-release-4-1.2.i386.rpm](http://mirror.centos.org/centos/4.1/os/i386/CentOS/RPMS/centos-release-4-1.2.i386.rpm "centos-release-4-1.2.i386.rpm")</span>
- **Tell YUM to upgrade your system**
- <span class="small">yum upgrade</span>