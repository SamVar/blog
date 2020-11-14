---
layout: post
author: "Samvel Vardanyan"
title: "Intsalling LAMP Stack"
date: 2020-11-13 02:35:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week we are going to install `LAMP` stack. LAMP stack is a set of software tools bundled together, it stands for Linux, Apache, MySQL and PHP, all of which are open source and free to use. It is the most common software stack that powers dynamic websites and web applications. First we need to istall Linux on our system, it can be Ubuntu, CentOS, Fedora etc. In this case I am installing Ubuntu desktop version. Next step we need to do i update our packages:
`sudo apt-get update && sudo apt-get upgrade -y`

\
**Installing Apache**

{% highlight ruby %}
sudo apt install -y apache2
{% endhighlight %}

After it’s installed, Apache should be automatically started. We can check the status by using the following command

{% highlight ruby %}
service apache2 status
{% endhighlight %}

Output:

![image](/blog/assets/images/apache-service.png)

If it’s not running, we can use `Service apache2 start` to start it.
To check Apache version: `apache2 -v`

To make sure that apache is working we can type our local IP address into browser and if we get the following screen it means apache is working.

![image](/blog/assets/images/apache.png)

\
**Installing MySQL**

To install MySQL we type the following command:

{% highlight ruby %}
$ apt-get install -y mysql-client
{% endhighlight %}

We can verify `MySQL` installation by typing the following command:

{% highlight ruby %}
$ dpkg --get-selections | grep mysql
{% endhighlight %}

Output:

![image](/blog/assets/images/mysql.png)

**Installing PHP**

We are going to install `PHP 7.4`

{% highlight ruby %}
sudo apt install php7.4 libapache2-mod-php7.4 php7.4-mysql php-common php7.4-cli php7.4-common php7.4-json php7.4-opcache php7.4-readline
{% endhighlight %}

Check PHP version information:

{% highlight ruby %}
php --version
{% endhighlight %}

After installing php we can restart apache sevice: `service apache2 restart`.
Of course there are lot of configurations that needs to be done but this is basic steps to get LAMP stack on your system.