---
layout: post
author: "Samvel Vardanyan"
title: "Hacking Website"
date: 2020-11-20 01:30:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week I am going to show how to hack a website. This was an assignment for my CIT 425 (Security) class, which I completed successfully. First and foremost we need to install [virtual box](https://www.virtualbox.org/) on our system since we are going to use virtual machine so we won't harm our system. Next up we need 2 VMs: [Metasplotable](https://information.rapid7.com/download-metasploitable-2017.html) and [Kali Linux](https://www.kali.org/). The installation for Metasploitable is very quick but Kali Linux requires some time. After we have both systems up and running on our VM we need to go to settings for each VM and put network adapters for each VM on `Host only Adapter` mode.
![image](/blog/assets/images/host-adapter.png)
The reason for doing this is to avoid any damage that we can cause our network, we eliminated both VMs from outside world.

\
**Creating Basic HTML Page**

Inside the Metasploitable VM, we need to make a web page as a basic HTML document. This web page should represent any information but need to consist of entirely static content. No backend language (such as PHP) nor any backend database (such as MySQL) is necessary. Keep it basic. Our mission is to replace the default web page in the Metasploitable VM for another site or we can just edit the html file and make some changes. So our mission is to use Kali Linux and hack Metasploitable in order to change the current html file that it has in its apache directory and put our html in that directory. So let's login into Metasplotable - default login and password: `msfadmin`. We can create basic HTMl file and put in `/var/www/html` directory, next we are going to start the Apache web server. Now we use metasploitable IP address in our web browser to make sure it can display our website.

\
**Hacking From Kali Linux**

Open the terminal on Kali and type `armitage`
![image](/blog/assets/images/armitage.png)

\
We leave ip address on local host and type user and password. Once we connected we need to start scanning for vulnerabilities. We go `Host - Nmap Scan - Intense Scan`

\
![image](/blog/assets/images/intense-scan.png)

\
After that’s done in the menu bar, we choose `Attacks – Find Attacks`

\
![image](/blog/assets/images/attack-analisys.png)

\
We are going to get a dialog box saying "Attack analysis is complete. Happy hunting!" This means we are ready to start our attack.

\
**Starting the Attack**

In the dasboard there are different hosts we can choose from. We need to choose metosplotiable machine in my case it has an IP address of 192.168.56.102 and right click on it choose “Attack – ftp – vsftpd 234 backdoor”. After that you’ll see a picture of “thunder” which means we have successfully attacked the Metasploitable host. We right click on attacked host and choose `Shell 1 - Interact` and now we gained root access into Metasploitable host.

\
![image](/blog/assets/images/root-access.png)

\
Now all we have left to do is to change the original website with ours. In order for us to destroy the original website and upload our website we go to directory: /var/www find the original index.html rename it or delete it and the upload our index.html right click on metasplotiable choose “shell – upload” and upload our index.html

\
![image](/blog/assets/images/upload-website.png)

\
Once uploaded next step is to change the ownership of the index.html file: `chown -R www-data:www-data index.html`. After we changed the ownership of the file, we open browser on our Kali Linux and type IP address of matsploitable in my case it is “192.168.56.102” And now we can see the hacked website. Metasplotable now has been hacked.

\
![image](/blog/assets/images/hacked-website.png)
