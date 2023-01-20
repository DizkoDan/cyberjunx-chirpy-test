---
id: 195
title: 'Passwordless SSH'
date: '2007-08-26T00:39:30-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/howtos/passwordless-ssh/'
---

This is a great way to perform automatic backups to a remote host over SSH. It requires shell access on both servers (obviously). Note that this is not the most secure way to do this, it is the easiest though.

1. Login to the server that you wish to connect **from,** as the user you wish to connect as**.** We’ll call this ***Server1***.
2. cd into ~/.ssh (you may need to create this directory).
3. Create  
    your RSA keys (we do not want to set a passphrase here, or we will be  
    prompted for it everytime we try to use it, which would defeat the  
    purpose):

1. **ssh-keygen -t rsa**
2. **\[enter\]**
3. **\[enter\]**
4. **\[enter\]**

4. You should now have 2 newly created files: id\_rsa &amp; id\_rsa.pub.
5. Copy id\_rsa.pub to the user you will be logging in as on your remote system. We’ll call this ***Server2.*** I usually use SCP.
1. **scp ~/.ssh/id\_rsa.pub remoteuser@server2:~/.ssh/server1\_id\_rsa.pub**

7. Login to ***Server2*** as the user from the above step.
8. cd into ~/.ssh
9. Add ***Server1*** to the users authorized keys file:
1. **cat server1\_id\_rsa.pub &gt;&gt; authorized\_keys**

11. Remove the key file &amp; change the permissions on your  
    authorized keys file (this will not work if the permissions are  
    incorrect).
1. **rm server1\_id\_rsa.pub &amp;&amp; chmod 600 authorized\_keys**

13. Logout, and try to login again from ***Server1***
14. That’s it!