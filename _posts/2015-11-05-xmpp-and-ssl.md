---
layout: post
title:  "Changes to XMPP and SSL"
date:   2015-11-04 12:13:01
categories: server
---
**TL;DR** Site now has SSL certificate; XMPP moved from port 443 to 993;

We have been invited to the beta of [Let's Encrypt](https://letsencrypt.org/), which means that Matrix.ac now has a valid SSL certificate. Yaay. 
This also includes your user directories. 

Now we serve up SSL web pages on port 443 this means that we can't use it for our XMPP server. So as of now we have moved from port 443 to 993.
The reason we run our XMPP server on both ports 993, and 5222 is to allow users to access the server from behind a firewall which might activity block the XMPP port. Port 993 is reserved for IMAP(S) and is normally allowed by most firewalls. It's also a restricted port number which means no user on matrix can impersonate it without having root access.
 
