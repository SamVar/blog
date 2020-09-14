---
layout: post
author: "Samvel Vardanyan"
title: "Docker Setup"
date: 2020-09-13 16:00:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week I setup a docker container which is pretty easy task. In order to do that first we need to install [docker](https://www.docker.com/) itself. Before downloading docker we can create an account and sign in. It use to be mandatory thing, but now you can download it without creating an account. In my case I already had an account and I simply downloaded the file and run the installer. After installation all I needed to do is to run it. Then I open the terminal and typed `docker ps -a` since I know there are no containers for right now. Now it's time to create a new container, so I followed the **Lab 1** instructions and created new container called **Cit480**:
{% highlight ruby %}
$ docker run -it -p 8080:80 --name cit480 ubuntu:18.04 bash
{% endhighlight %}
So here we are creating a container called **cit480**, mapping port 8080 to port 80 inside of our container and pulling ubuntu image and running in interactive mode with bash. now once we have container created we need to run it so we can install **LAMP** stack. It stands for *Linux, Apache, Mysql, Php*. 
First thing we need to do is to start our newly created Ubuntu container. We issue the following commands: 
{% highlight ruby %}
$ docker start cit480
$ docker exec -it cit480 bash
{% endhighlight %}
This is what it's going to like:
![image](/blog/assets/images/dockerContainer.png) and now we are inside of our container. Now it's time for us to install \*\*LAMP\*\* stack, but before doing that we need to update our packages and install `nano` text editor, so we run:
{% highlight ruby %}
$ apt-get update
$ apt-get upgrade
{% endhighlight %}
and then install `nano` text editor:
{% highlight ruby %}
$ apt-get install nano git curl zip
{% endhighlight %}

\
It's time to install **Apache** inside our container:
{% highlight ruby %}
$ apt-get install apache2
{% endhighlight %}

To make sure it's installed correctly we are going to start apache:
{% highlight ruby %}
$ service apache2 start
{% endhighlight %}

\
Now we open browser and type `localhost:8080` we should be able to see the following screen on our browser:
![image](/blog/assets/images/apache.png)

\
Next step is to install `MySQL` and to install it we run the following command:
{% highlight ruby %}
$ apt-get install -y mysql-client
{% endhighlight %}

\
And lastly we install Php:
{% highlight ruby %}
$ apt-get install -y php libapache2-mod-php php-mysql php7.2-cli php7.2-curl php7.2-gd php7.2-mbstring php7.2-mysql php7.2-xmlphp-xml
{% endhighlight %}

So we successfully installed **LAMP** stack inside of our container.

The problem that I'm having with my container is that I have created my container and installed **LAMP** stack on my desktop computer and that's where I work all the time, but sometimes I need to work on my laptop while I'm on the go so having everything only on my desktop makes harder to do so. I haven't been able to find solution to synchronize docker between my desktop and laptop computers. But I was able to find another solution to that problem instead. Basically what we can do is to back up the container on my desktop and make a backup file and transfer it to my laptop and load it from that file. Here's how to do it: on the desktop computer inside of our container we type the following command:
{% highlight ruby %}
$ docker commit -p <container-ID> <backup-name>
$ docker save -o <backup-name.tar> <backup-name>
{% endhighlight %}

![image](/blog/assets/images/dockerBackup.png)

\
And this is the actual backup file that we created:

![image](/blog/assets/images/dockerBackupImage.png)

\
Once we have the backup file we go to laptop computer and load it there. We can copy the file on a flash drive and transfer to another computer. In my case because both my computers are using the same apple ID, I don't need to transfer it, it automatically shows up on my laptop. On my laptop I run the docker open the terminal and type the following command:

{% highlight ruby %}
$ docker load -i <backup-name.tar>
{% endhighlight %}

\
![image](/blog/assets/images/dockerLoad.png)

\
Now we type the second command:

{% highlight ruby %}
$ docker run -it --name <new-name> <backup-name>
{% endhighlight %}

\
![image](/blog/assets/images/dockerRestore.png)

And finally we have the exact same container running on both systems and if we do `docker ps -a` we'll see that we have the same `cit480` container running on both systems.

\
![image](/blog/assets/images/dockerPS.png)
