---
layout: post
author: "Samvel Vardanyan"
title: "OpenVPN Setup"
date: 2020-10-15 01:45:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week we are going to install OpenVPN on Raspberry Pi 4 using PiVPN and access it from anywhere on the world. This is very similar installation of WireGuard VPN since they both are part of PiVPN. They just have slightly different steps, but in general both openVPN and WireGuard share a lot of similarities since they are part of PiVPN project.

\
**Installing RaspberryOS**

Next thing we need to do is to download and install [RaspberryOS](https://www.raspberrypi.org/downloads/) on micros SD card. Once it is installed on SD card we can put SD card into Raspberry Pi and boot from SD card. After the first boot we need to update our system to make sure we have latest updates on our system, to do so open the terminal and type:
{% highlight ruby %}
sudo apt-get update && sudo apt-get upgrade -y
{% endhighlight %}

\
**Installing OpenVPN**

The next step is to install [PiVPN](https://www.pivpn.io/), open Terminal on your Raspberry Pi and run the command below, which will execute a script to install PiVPN.

{% highlight ruby %}
curl -L https://install.pivpn.io | bash
{% endhighlight %}

\
\
Wait for the process to install the necessary packages. When it’s done, you will be brought to a screen that will inform you that PiVPN will allow you to install OpenVPN or WireGuard on a Raspberry Pi. Select OK.

![image](/blog/assets/images/vpn-installer.jpeg)

\
\
You will now need to select which VPN you would like to install. In my last blog we have already talked about installing WireGuard, this time we are installing OpenVPN, elect OpenVPN and hit OK.

![image](/blog/assets/images/wireguard.jpeg)

\
\
You will now be prompted to use your public IP address or public DNS entry. If you have a static IP address, you are free to use this address. However, if you have a dynamic external IP address, you will need to set up DDNS. If you selected to use a dynamic DNS address, you can enter that information here.
\
For the next few steps, the default settings are fine for most users. You'll be asked whether you want to use UDP or TDP (you should choose UDP unless you have a good reason for not doing so), what port you want to use (1194 is fine unless something else is using it), and what DNS provider you want to use, I always use `Google` as my DNS.
\
Choose the recommended security certificate when prompted—larger sizes grant better security, but can slow things down and aren't necessary for most users. Enable unattended upgrades, and PiVPN will install the necessary packages and create the necessary configuration files.

\
![image](/blog/assets/images/unattended.jpeg)

\
**Configuring OpenVPN**

Reboot the system. After rebooting, you’ll need to open a Terminal window and run:

{% highlight ruby %}
pivpn add
{% endhighlight %}

Give the configuration file a name, set how many days the certificate lasts, and enter a password of your choice. It'll generate an .ovpn file for you under /home/pi/ovpns, which you'll need to connect to your VPN—copy it to your PC and keep it somewhere safe.

If you're using a dynamic DNS service, open the file in Notepad, and replace your IP address in line 4 with your custom URL.

\
![image](/blog/assets/images/openVPN.png)

\
**Port Forwarding**

We now need to port forward UDP port 1194 on our router to our Raspberry Pi. Create a port forwarding rule for UDP port 1194 to your Raspberry Pi’s IP address.

\
**Connect to Your VPN**

OpenVPN has an official client called OpenVPN Connect, which is available on Windows, macOS, Linux, iOS, and Android. Download the app and launch it, click the "File" tab to add a new profile. Navigate to the configuration file you copied from the Pi and select it. Click the Add button, and you can connect to your VPN by flipping the toggle switch on and entering your password.
