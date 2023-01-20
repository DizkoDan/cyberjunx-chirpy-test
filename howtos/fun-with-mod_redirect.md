---
id: 646
title: 'Fun with mod_redirect'
date: '2009-01-30T15:29:54-04:00'
author: DizkoDan
layout: page
guid: 'http://www.cyberjunx.com/blog/?page_id=646'
aktt_notify_twitter:
    - 'no'
---

For [serve-you.net’s](http://www.serve-you.net) user’s site, I wanted all of the site to be SSL for obvious reasons. There’s no actual content available under the non SSL docroot. However, I thought it would be helpful to redirect non SSL requests to the site. This can be easily accomplished with a one liner in PHP:

> 

Easy enough, but I decided that I wanted to be a little more helpful than that, and actually redirect the requested page as well if possible. So if for instance someone wants to go to the [Domain Checker](https://users.serve-you.net/domainchecker.php), and forgets the https, they would be forwarded to the correct location.

This is incredibly easy to accomplish with [mod\_rewrite](http://httpd.apache.org/docs/2.0/mod/mod_rewrite.html). Create a .htaccess file in the root directory that you wish to redirect, or use a Directory tag in the httpd.conf. The following code is all that it takes:

> RewriteEngine On  
> RewriteCond %{SERVER\_PORT} 80  
> RewriteRule ^(.\*)$ https://users.serve-you.net/$1 \[R,L\]