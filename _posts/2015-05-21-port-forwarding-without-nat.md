---
layout: post
title:  "Port forwarding without NAT support"
date:   2015-05-21 11:34:01
categories: server
---
When setting up our XMPP server we ran into an issue with NAT port forwarding, it turns out that our kernel version does not have support for iptables NAT-ing. This meant that we could not forward port 443 to 5222 for users stuck behind firewalls, boo. We spent a while looking for a method which can help us, we could setup xitend/rinetd but these were a bit unmaintained. We could have told our XMPP server to listen on 443, but that would require running our server as root, which sounds scary.

So we decided to have a look at a tool called [SOCAT](http://www.dest-unreach.org/socat/) which is like [netcat](http://nc110.sourceforge.net/) but better, they said it not me. What SOCAT does is listen on port 443 and forward all traffic to 5222, simple sockets. It does need to run as root, but appears to be well maintained. Below creates the TCP tunnel: 

	socat -d -d -lf /var/log/xmpp-443 TCP4-LISTEN:443,fork,bind=178.62.58.156 TCP4:127.0.0.1:5222

Now this outputs any errors to the /var/log/xmpp-443 file, and binds to IPv4 178.62.58.156 on port 443 and forks any connection which it receives (so that it can handle more than one at a time) then forwards the data to localhost port 5222. 

We can put this into a little init.d script so that it starts up at boot time and allows us to start and stop the tunnel.

**[TODO: Include links to repo]**

And there you have it port forwarding with out iptables NAT. One day we will update our kernel. 


> Block quote

Something ```Some inline pre``` text


{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}