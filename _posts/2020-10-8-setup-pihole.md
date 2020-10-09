---
layout: post
author: "Samvel Vardanyan"
title: "Setup Pi-Hole"
date: 2020-10-08 20:00:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**What is Pi-Hole Ad Blocker?**

Pi Hole ad blocker is a piece of software that runs at the network level. As the name suggests, it's intended for use on the Raspberry Pi and other embedded devices. However, virtually any Linux machine should be able to run Pi-Hole. Benefits of running Pi hole include its ability to block ads on gadgets like mobile OSes and smart TVs. Basically, Pi-Hole is a sinkhole server, or a Blackhole DNS. At its most basic, a DNS server is a registry containing public IP addresses and corresponding hostnames. Upon visiting a website, there's a query to the DNS server which looks up the IP address, or location, of the server. A DNS sinkhole is a DNS server which distributes fake results to any systems searching for DNS information. Aside from this functionality, Pi-Hole has the ability to work as a DCHP server.Pi-Hole replaces your current DNS server and blocks tracking domains as well as ads. 

**How does Pi-Hole Work?**

This private DNS server intercepts ad-serving domain queries and denies access. As such, no advertisements are downloaded. You'll largely see the exact same page, albeit sans ads. The network-wide ad blocking software sits between client devices, like your computers, mobile devices, and smart TVs. Pi-Hole thus blocks requests to ad servers. Since Pi Hole is free, easy to set up, and blocks over 100,000 ad-serving domains, it's a powerful tool. You'll benefit from enhanced network performance. 

**What do we need to set up Pi-Hole**

Raspberry Pi board 
Raspberry Pi PSU
Micro SD card
Raspberry Pi case
Raspberry OS
Peripherals (keyboard, mouse)
Image mounting software


**Installation**

We need to do is to download and install [RaspberryOS](https://www.raspberrypi.org/downloads/) on micros SD card. Once it is installed on SD card we can put SD card into Raspberry Pi and boot from SD card. After the first boot we need to update our system to make sure we have latest updates on our system, to do so open the terminal and type:
{% highlight ruby %}
sudo apt-get update && sudo apt-get upgrade -y
{% endhighlight %}

Now once we have OS installed and up to date, it is time to install Pi Hole. Open terminal and type 

{% highlight ruby %}
wget -O basic-install.sh https://install.pi-hole.net
sudo bash basic-install.sh
{% endhighlight %}

After that, you'll see a notification that the Pi Hole automated installer is running. Press ok an continue. 

Next up, there's a donation screen. Again, click ok and slog on. 

Because Pi Hole is a server, it requires a static IP address. We need to configure our network settings (DHCP). Hit ok. 

Now, pick your interface, Ethernet or Wi-Fi. Highlight eth0 (ethernet) or wlan0 (Wi-Fi), press the spacebar to select the proper option, and press ok. 

It's time to select your upstream DNS provider. You can pick from Norton, Comodo, DNSWatch, Quad9, FamilyShield, Cloudflare, or a custom DNS server. Pick your preferred option and continue.

Pi-Hole uses third-party lists for ad blocking. By default, it doesn't block any ad-serving domains. Therefore, you'll need to toggle these on. We need to select the block lists we'd like to use by highlighting options and hitting the spacebar. These include StevenBlack's Unified Hosts List, Cameleon, ZeusTracker, Disconnect.me Tracking, Disconnect.me Ads, Hosts-file.net Ads, and MalwareDomains. When finished, press ok, and proceed.

Lastly, we review our network settings. We'll see our IP address and gateway. The gateway IP address is our router's IP address, and the IP is that of our Raspberry Pi PiHole setup. If all looks good, hit yes. 

Pi-Hole will display a warning about an IP conflict. This shouldn't occur, but peruse the message and hit ok. 

You'll be asked if you'd like to install the web admin interface. On is recommended, but you can decline installation of the Pi Hole web interface. The Pi-Hole web UI allows you to remotely manage Pi Hole. 

Now, Pi Hole asks if you want to log queries. I'd recommend leaving this on. Pick your preference and click ok. 

Finally, we'll see a message that installation is complete. At the bottom is the web interface, available at `http://pi.hole/admin` or `Ip address/admin`. The password is at the bottom too. We can check that Pi Hole is running by entering pi hole status in a command prompt. 

**Pi-Hole Configuration**

With Pi Hole properly installed on our Raspberry Pi, it's time to configure Pi-Hole. For whole-home ad blocking with PiHole, we'll need to manually edit our DNS settings. Here, instead of the default DNS, we input our PiHole Raspberry Pi's IP address. 

To access the Pi-Hole web UI, navigate to `http://Pi-Hole device IP address/admin/` and login using the default Pi Hole password. We'll see the PiHole web interface. On the side, there are tabs for a dashboard, query log, long term data, whitelist, blacklist, tools, settings, and more Under settings, we'll find another block lists tab where we can add third-party block lists. It's an incredibly powerful tool capable of much customization. 