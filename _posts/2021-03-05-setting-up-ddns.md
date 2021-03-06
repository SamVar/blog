---
layout: post
author: "Samvel Vardanyan"
title: "Setup DDNS"
date: 2021-03-05 18:30:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

In this post I am going to talk about how to set up DDNS service on your router.

**What is DDNS ?**

DDNS stands for Dynamic DNS Services. It is used by small companies and individuals when they want to publish a service on the Internet, and that service is hosted within an internal or home network. Home networks typically use a NAT router to connect to the internet which means that devices located on the internal network aren’t accessible from the Internet. For instance I need to setup DDNS service in my home network because I have VPN server setup in my house and in order to access my VPN services from outside I always need to remember my house's public IP address because my VPN is behind that public IP address. Well that's not a problem to remember one IP address only. But what if my home's public IP address gets changed since it is not a static IP. In that case I will loose access to my home network from outside. That's where DDNS comes into play.

**How does it work ?**

With Dynamic DNS we assign the web server or our home network a fixed name. Then we assign our IP address to that name. So now when we use the fixed name it is directly associated with our public IP address. But what if our IP address changes? We need periodically update the DNS record. But that is not very reliable, instead what we can do is to automatically update the DNS server records so it points to our new IP address in case if it gets changed.

**Setup DDNS**

Before we can enable Dynamic DNS we will need an account from a DDNS provider. In my case I went with provider called [NO-IP](https://www.noip.com/). After we create an account with them we need to choose `Create a Hostname`. Now we need to fill out all the fields. For the `Hostname` tab we can choose any hostname that we like. `Domain` we can leave under `ddns.net` for `IPv4 address` we going to enter our public IP address. Everything else stays the same, click `Create Hostname`.

![image](/blog/assets/images/no-ip.png)

**Change Router Settings**

Once we done with setting up our DDNS with provider it is time for us to change our router settings so it can recognize any IP changes. I am using `Lynksys ea9500` router. So all I need to do is to open my routers home page log into my router's settings page and navigate to `Security -> Apps and Gaming`. Once I'm here under `DDNS` tab we select our provider which is `NO-IP` then we fill out our login and password credentials from NO-IP website (this is the same login and password that we use to login into our NO-IP account) then we fill our hostname that we choose during our registration. Once we click apply we will see `status Success`.

![image](/blog/assets/images/router-no-ip.png)

We have successfully setup `DDNS` service and now we are using our hostname which points to our IP address, to communicate to our home network. If our IP address gets changed our hostname will update our record to point to the right IP address.
