---
layout: post
author: "Samvel Vardanyan"
title: "Setup WiFi Bridge"
date: 2020-10-18 19:40:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week we are going to setup a WiFi bridge. To do this we need 2 routers a laptop and an Ethernet cable.

**Setting Up the First Router**

1. Connect your router to your broadband modem using the WAN port and turn your router on. Then connect the ethernet cable to LAN port of the router and the other end connect to your laptop.

2. Go to the management web page for the router. Open a browser and enter the IP address of the router administration page. This is usually something like 192.168.1.1. 

3. Change the default administrator password and username for the router. This setting is usually found in the router administration page in a tab or section called Administration. Use a strong password that you won't forget.

4. Add WPA2 security. This step is essential. Find this setting in the wireless security section of the router administration page. Select which type of encryption to use and enter a passphrase of at least 8 characters. The more characters and the more complex the password, the better.

![image](/blog/assets/images/first-router-wifi-setup.png)

{:start="5"}
5. Change the wireless network name (SSID). To make it easy for you to identify your network, choose a descriptive name for your SSID in the wireless network information section of the router administration page.

6. Save all settings and reboot your router. Once rebooted connect your laptop to your router wirelessly using the SSID and password that we created.

**Setting Up the Second Router**

Now when we setup the first router as our main WiFi router it is time to setup the second router as a bridge.

1. First thing we need is to remember all existing wireless settings from our main router. We can write it down on piece of paper so we won't forget.

2. We will connect the bridge router directly to our laptop with an ethernet cable, then we will disable the laptop’s wifi connection, which will ensure our laptop is only talking to the router. 

3. Open a web browser and go to the bridge router’s administration page at 192.168.1.1 then we will be prompted to enter router's default password, it is usually admin/admin.

4. In the `Wireless settings` section, we will set a new SSID, then we will set all of the other settings on this page to match our primary router. After making these changes, we will be prompted to reboot the router, which we must do to ensure these changes take effect. 

5. After reboot, open the router management console and select `Network/LAN` section. We will see here that our router has default IP address of `192.168.1.1`. We are going to change it to `192.168.1.2` to avoid IP conflicts in our network. 

6. In `Wireless Settings` section we need to tick the checkbox `Enable WDS Bridging` this will open drop-down section and we will need to fill in the `SSID` and `BSSID sections.` Now we enter the wireless security values from our main router and `Save` the settings.

7. It is important to disable `DHCP` since our main router will handle that. We open `DHCP` section and set it to `Disable`, and save changes. 

8. Disconnect the ethernet cable from your bridge and reboot. After reboot in your laptop we should be able to see both main SSID of our first router and BSSID of our bridge. 

Now once he have bridge setup we can connect to our router and do some testings to make sure that our setup works correctly. If we need to manage our main router we use IP address of `192.168.1.1` and for wireless bridge management we use IP address `192.168.1.2`