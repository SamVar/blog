---
layout: post
author: "Samvel Vardanyan"
title: "Hosting Website"
date: 2021-02-24 17:30:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

In the first part I talked about how I built a website what technologies I used and presented the final version of the website. In this part I am going to talk about how to host already ready website. In order to do so first we need domain name so the user can type it in browsers address bar and connect to our website, then we need to decide which hosting company we are going to use and finally we need to reroute our domain to our hosting website. 

**Hosting**

Before purchasing domain name and hosting our website we need to minify our code. This is done to make the file sizes smaller and dramatically improves website load time. I used website called [minifier.org](https://www.minifier.org/) to minify all my HTML CSS and JS files. After minifying our code next step is to purchase a domain. I purchased my domain from [google domain](https://domains.google/). I choose the name [Moonguide.net](https://moonguide.net/). For hosting I choose [Dreamhost](https://www.dreamhost.com/) since they had best price available at the moment. So I purchased domain name and annual hosting plan with [Dreamhost](https://www.dreamhost.com/). Everything is ready the only thing is left to do is make sure we can point google domain to dreamhost. To do that we need to mess with some of the settings in google domain website. 

**Setting up DNS**

We need to point google domain to dreamhost servers so when user types our domain in address bar they can connect to dreamhost servers. To do that we open our google domain page and login. Under DNS submenu we change Name servers from `Use the Google Domains name servers` to `Use custom name servers`. Under `name server` we add 3 DNS servers: `ns1.dreamhost.com`, `ns2.dreamhost.com` and `ns3.dreamhost.com`.


\
![image](/blog/assets/images/dreamhost-dns.png)

\
Once this is done every time user types the domain name in address bar they will be redirected to [Dreamhost](https://www.dreamhost.com/) servers where our website files are going to be and this is the last step to upload our files into dreamhost servers. All we need to do is to login into our [Dreamhost](https://www.dreamhost.com/) account and click upload. Then we upload all our files and click save. After saving the files we just need to give it a couple of minutes for changes to take affect. We can verify if our website is up and running by typing our domain name into address bar. Congratulations, we now have fully functional and working website available to public. 