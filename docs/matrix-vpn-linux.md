---
layout: page
title: Linux VPN Guide
permalink: /docs/vpn-linux/
resource: true
categories:
- VPN
---

Within 24 hours of creating an account on matrix.ac and making a request for VPN access (but usually much sooner) you will receive an OpenVPN connection profile that you can use to connect to our VPN.

Download your OpenVPN Configuration File
-------------------------

The first thing to do is download the OpenVPN connection profile. It will have an .ovpn file extension and will typically have your username as the filename. You can download this using the following scp command:

	scp matrix.ac:username.ovpn .

which will download the profile to your current working directory. 

Install OpenVPN
---------------

Next you need to install the OpenVPN client to use this file to connect to the matrix.ac VPN. As we use OpenVPN, the OpenVPN client is an easy and straightforward way of connecting to it. On Linux based systems you can usually get the OpenVPN package from your package manager. For example, if you are running Debian or Ubuntu, you can install openvpn with the following command:

	sudo apt-get install openvpn

This is all you need to make use of your free matrix.ac VPN.

Start the VPN
-------------

Finally, you can open your connection to the VPN with the following:

	sudo openvpn --config username.ovpn

Just press `Ctrl+C` when you are finished using the VPN and it will shut down.



If you ever lose access to your .ovpn configuration file please let us know as soon as possible. In such an event we will revoke your current profiles access and issue you another profile.

