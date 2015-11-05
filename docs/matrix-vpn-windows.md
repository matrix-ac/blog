---
layout: page
title: Windows VPN Guide
permalink: /docs/vpn-windows/
resource: true
categories:
- VPN
---

Within 24 hours of creating an account on matrix.ac and making a request for VPN access (but usually much sooner) you will receive an OpenVPN connection profile that you can use to connect to our VPN.

The first thing to do is download the OpenVPN connection profile. It will have an .ovpn file extension and will typically have your username as the filename. 
There are a number of ways of downloading this file.

The easiest method uses the FileZilla GUI program. If you have [pageant](http://the.earth.li/~sgtatham/putty/latest/x86/pageant.exe) already setup with your SSH key, FileZilla will make use of this to provide you with a graphical way of transferring files to and from the matrix.ac server. If pageant isn't already set up, download it from the above URL (you can also verify it), and launch it. It should appear as an icon in your notification area. From here right click and select Add Key, choosing your SSH private key (the one without .pub).

With this setup you can now move onto the next step of downloading the .ovpn profile needed to access the VPN to your local computer.

Download FileZilla Client
---------------------

As mentioned before, the easiest way for a new user to download this is using FileZilla. You can download FileZilla from the following URL <https://filezilla-project.org/download.php?show_all=1> 

Once downloaded and installed, run Filezilla, entering your username in the username box, and matrix.ac in the host box. Leave the password field blank and enter '22' as the port and click quickconnect. We leave the password blank as for security reasons the matrix.ac server doesn't accept passwords, but rather uses your SSH key for authentication.

On the right hand pane you should see a listing of your files on matrix.ac. One of them will be the required 'username.ovpn' file. You can drag this to the appropriate directory on your local computer on the left hand pane. Lets transfer it to your Desktop.

This is all we need FileZilla for. So you can uninstall it if you want.


Download OpenVPN
-----------------------------
The OpenVPN software will read the downloaded .ovpn profile and connect you to the matrix.ac VPN.
The software can be downloaded [here](https://openvpn.net/index.php/open-source/downloads.html).
It is recommended, but optional, to verify the downloaded software. You can find out how to do this at the following URL <https://openvpn.net/index.php/open-source/documentation/sig.html>

Now that you have the OpenVPN software downloaded (and hopefully verified) you can install it. It will ask you to install some drivers required for it to function.

Updating the OpenVPN Configuration
-------------------------

Once you have the username.ovpn file downloaded, and OpenVPN installed, you have to place the .ovpn file in the following directory on your computer.

	C:\Program Files\OpenVPN\config\

Once done, run the OpenVPN GUI client (as an adminstrator) installed earlier and you should see an icon appear in your notification area. Right click this and choose connect.

If you ever lose access to your OpenVPN configuration profile please let us know as soon as possible. In such cases, we will revoke your current profiles access and issue you another profile.
