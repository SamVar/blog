---
layout: post
author: "Samvel Vardanyan"
title: "Intsalling Nginx"
date: 2021-04-09 12:30:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

Nginx is one of the most popular web servers in the world and is responsible for hosting some of the largest and highest-traffic sites on the internet. It is more resource-friendly than Apache in most cases and can be used as a web server or reverse proxy. Today I will discuss how to install Nginx on your Ubuntu 18.04 server.

\
**Installing Nginx**

First we will update our local package index so that we have access to the most recent package listings. Afterwards, we can install nginx:

{% highlight ruby %}
sudo apt update
sudo apt install nginx
{% endhighlight %}

This will install Nginx and any required dependencies to our server.

\
**Adjusting the Firewall**

Before testing Nginx, the firewall software needs to be adjusted to allow access to the service. Nginx registers itself as a service with ufw upon installation. First we need to list the application configurations that ufw knows how to work with by typing:

{% highlight ruby %}
sudo ufw app list
{% endhighlight %}

Output:

{% highlight ruby %}
Available applications:
  Nginx Full
  Nginx HTTP
  Nginx HTTPS
  OpenSSH
{% endhighlight %}

Here we need to allow traffic on port 80, we enable it by typing:

{% highlight ruby %}
sudo ufw allow 'Nginx HTTP'
{% endhighlight %}

then we can verify by typing:

{% highlight ruby %}
sudo ufw status
{% endhighlight %}

Output:

{% highlight ruby %}
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Nginx HTTP                 ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Nginx HTTP (v6)            ALLOW       Anywhere (v6)
{% endhighlight %}


\
**Checking Web Server**

We can check with the systemd init system to make sure the service is running by typing:

{% highlight ruby %}
systemctl status nginx
{% endhighlight %}

Output should be something like this:

{% highlight ruby %}
nginx.service - A high performance web server and a reverse proxy server
   Loaded: loaded (/lib/systemd/system/nginx.service; enabled; vendor preset: enabled)
   Active: active (running) since Fri 2021-04-09 16:08:19 UTC; 3 days ago
     Docs: man:nginx(8)
 Main PID: 2369 (nginx)
    Tasks: 2 (limit: 1153)
   CGroup: /system.slice/nginx.service
           ├─2369 nginx: master process /usr/sbin/nginx -g daemon on; master_process on;
           └─2380 nginx: worker process
{% endhighlight %}

This means that the service have started successfully. We can type our server’s IP address into our browser’s address bar to load the page:

\
![image](/blog/assets/images/nginx.png)