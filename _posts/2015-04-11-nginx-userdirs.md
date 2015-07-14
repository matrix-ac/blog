---
layout: post
title:  "NGINX and userdirs"
date:   2015-04-11 11:34:01
categories: server
---
We want good old fashion user directories, this is the little tilde before your name on your URLs. like `https://matrix.ac/~osaka`. The files for this are stored in `/home/oska/public_html`. 

To have this working in NGINX, you need to add the following to a virtual host config.

	location ~ ^/~(.+?)(/.*)?$ {
		alias /home/$1/public_html$2;
	}

This simple says if the location requested contains a ~ and some text look in the directory /home/some text/public_html.
 
