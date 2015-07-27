---
layout: page
title: How to connect with SSH (Linux)
permalink: /docs/ssh-linux/
resource: true
categories:
- Command Line
---

Secure Shell (SSH) allows you to run commands on a remote computer securely and nearly all Linux distributions come packaged with an SSH client. SSH uses public key cryptography to authenticate the user with the server. This means that you will need to generate a key pair, one public and one private. You can also use passwords, but these are less secure.

The private key is stored on your machine and should never be lost or given to another person as the private key is what gives you access to the server and what identifies you as you. The public key is used for the server to verify that you are who you claim to be. You need to give us your public key so that the server can verify you.

## Generate Keypair

To generate your key pair you need to run the command 'ssh-keygen', it will ask where you want to save your keys, you can hit enter to use the default or you can enter a name and location for the keys. **Always store your keys in ~/.ssh**, this is to make sure that no other users have access rights to your keys.

You should also provide a passphrase for your keys which you will need every time you wish to use them. If you want it can be blank but it's a good idea to set a passphrase to prevent unauthorized access. 



	osaka@ubuntu:~$ ssh-keygen 
	Generating public/private rsa key pair.
	Enter file in which to save the key (/home/osaka/.ssh/id_rsa): /home/osaka/.ssh/matrix.ac 
	Enter passphrase (empty for no passphrase): 
	Enter same passphrase again: 
	Your identification has been saved in /home/osaka/.ssh/matrix.ac.
	Your public key has been saved in /home/osaka/.ssh/matrix.ac.pub.
	The key fingerprint is:
	32:99:95:1f:9e:4f:da:17:8b:2e:ba:1a:f0:dd:64:1e osaka@ubuntu
	The key's randomart image is:
	+---[RSA 2048]----+
	|                 |
	|         .       |
	|        o .      |
	|       + o o     |
	|    . = S E . .  |
	|     o + = * . o |
	|      o . + + o  |
	|       .  .. .   |
	|      ..oo ..    |
	+-----------------+
	osaka@ubuntu:~$ 

Now that you have your keys generated you need to send us your public key. In the example above the public key is stored in ```/home/osaka/.ssh/matrix.ac.pub```. Copy and paste that into the [join](/join) form. 

	osaka@ubuntu:~$ cat /home/osaka/.ssh/matrix.ac.pub
	ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDCSQrjDCG1l8J7lJrrvaWyKWTulLXCZLDd3YTKOg8Lsw2LAtEdEHuQEiKhQUoyxeSRB17rMWBm2+Sqh1rE68bBpiyjPPk+Pcu6FJcPYR/hFKXdxTzP9vEsMYVfE4XizkqgpYT78q4aSESBc1XiNSNLOxvc1kr5OfhzmpZuYeDC8/TGpXO1QqbP/oRas9zqi+o9eYhA3GE4u7Mc+IZLkzjtVm8Ig+DZVx+Ky4b9s8TIpx4wJXzuU74xsHY2G1b0IFnVJCfU/EPGfqbkPt4NVN9MfilkltWGla0sLacwnKNBxu9fDi3ahoAyvfNIkvbBLByfWgX/x6MDzQK/12IY4JBj osaka@ubuntu

Make sure you have activated your account, via the email link, and you should be able to login with the following SSH command: 

	ssh osaka@matrix.ac -i ~/.ssh/matrix.ac

When you first connect you will be asked to check the fingerprint of the server. What this means is that are you sure this is the matrix server. So check the fingerprint you see with the one below and if they match that's good news, go a head and types yes.

	The authenticity of host 'matrix.ac (178.62.58.156)' can't be established.
	ECDSA key fingerprint is 73:a5:14:b0:ec:dd:2d:50:fa:c0:df:8b:5f:20:0f:0c.
	Are you sure you want to continue connecting (yes/no)? 

> You need to make sure that you never ignore this message, it could be someone impersonating the matrix server.

If you set a passpharse you will be prompted to enter that now, if not you will be connected to the matrix via secure shell. 

	osaka@ubuntu:~$ ssh osaka@matrix.ac -i  ~/.ssh/matrix.ac
	The authenticity of host 'matrix.ac (178.62.58.156)' can't be established.
	ECDSA key fingerprint is 73:a5:14:b0:ec:dd:2d:50:fa:c0:df:8b:5f:20:0f:0c.
	Are you sure you want to continue connecting (yes/no)? yes
	Warning: Permanently added 'matrix.ac,178.62.58.156' (ECDSA) to the list of known hosts.

	        ===== NO UNAUTHORIZED ACCESS =====
	                You've been warned!

	Enter passphrase for key '/home/osaka/.ssh/matrix.ac': 
	Linux matrix 3.2.0-4-686-pae #1 SMP Debian 3.2.65-1+deb7u1 i686
	                                     _.----.
	        ____________________________'       `.
	       (____________________________         ;
	                                    '-.____.' 
	                There is no spoon.

	You have new mail.
	Last login: Mon Jul 27 10:12:45 2015 from 127.0.0.1
	osaka@matrix:~$ 

## SSH Configuration file

That is a long command to remember you might want to use SSH's configuration file to help you remember the command. Create the file ~/.ssh/config, and enter the following at the top of the file: 

	Host matrix
		HostName matrix.ac
		Port 22
		User osaka
		IdentityFile ~/.ssh/matrix.ac

Now you can use the command ```ssh matrix``` to connect.

## SSH-Agent

If you have set a long passphrase and do not wish to keep entering it every time you want to connect to the server, you can use SSH-Agent to store your passphrase while you are logged in on your computer. 

Start the ssh-agent in the background:

	eval "$(ssh-agent -s)"
	# Agent pid 59566

And add your key to the ssh-agent, you will be prompted to enter your passphrase: 

	ssh-add ~/.ssh/matrix.ac
	# Enter passphrase for /home/osaka/.ssh/matrix.ac: 
	# Identity added: /home/osaka/.ssh/matrix.ac (/home/osaka/.ssh/matrix.ac)


Done. Now connect with ```ssh matrix``` and you should not have to enter your passphrase. You can extend this by using programs like gnome-keyring/seahorse, keychain and other key managers.

