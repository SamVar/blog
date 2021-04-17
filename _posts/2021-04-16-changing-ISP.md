---
layout: post
author: "Samvel Vardanyan"
title: "Changing ISP"
date: 2021-04-16 11:30:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

This week I am going to talk about how I changed my Internet Service Provider, what issues I faced after changing it and what I did to resolve those issues. I have Spectrum in my house, their ultimate Internet which provides 400Mbps download and 20Mbps upload. It works fine the only problem I was having is their upload speed which is only 5 percent of their download speed. Upload speed is very important to me since all the classes are online and you need to have good upload speed to use Zoom, Discord or any other program that requires higher upload speeds.  So I decided that I want higher upload speed and the only option in my area was Frontier which offers fiber optic connection and symmetric upload and download speeds. So I went ahead canceled my spectrum and subscribed for Frontier's fiber optic 500Mbps download and 500Mbps upload package. 

\
**Issues Faced**

After Frontier's technician installed all fiber wires he then installed the fiber ONT/Modem and connected to my router. I checked the speed for my new internet and I really got 500Mbps Down and 500Mbps Up which was great. Now the only problem is that I get full speed only if I am connected via ethernet cable, but when I connect through wifi the speed goes to half even if I am very close to the router and using only 5Ghz band. When I was using spectrum's Ultimate internet I was able to get full speed 400Mbps through the same router on the 5Ghz band, but now even though nothing has changed we only added one modem to get more than 200Mbps speed through the same wifi and same 5Ghz band is impossible. I can't even blame to my new ISP since I get full speed when I use ethernet cable. So I figured something was wrong with my router. 

\
**Steps to Solve the Issue**

I filtered everything down to my router. So, to solve the issue first thing I did was to reboot the router, that didn't seem to solve the issue. Then I decided to change wifi channel to minimize the interference, that didn't help as well. Then I decided instead of going to every and each settings, to reset the router and see if that helps. Unfortunately, it didn't help and I was still getting slow speeds and dropped connection. I had only one thought in my mind and that was something was interfering with my router. But, because previously I didn't have this problem and it began after installing fiber modem I though maybe the modem is interfering with my router. To confirm that there is something wrong with wifi connection I started to ping my router from my laptop. Usually it takes 2 ms to receive a response from my router, but this time it was doubled in some cases even tripled. So, that proved that there was interference. The modem was installed next to  my router and it had a huge power brick. What I ended up doing was moving the power brick and the modem one shelf lower and run cat 6 from there to  my router. It was moment of truth, I run another speed test and guess what. I got full speed.

\
![image](/blog/assets/images/speedtest.png)

And that's how I was able to find the issue and resolve it. 