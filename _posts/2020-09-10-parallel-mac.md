---
layout: post
author: "Samvel Vardanyan"
title: "Parallel for Mac"
date: 2020-09-10 12:00:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Installing Parallel Desktop for Mac**

This week we are going to install Parallel for Mac on Mac OS, so we can run Windows, Linux or any other operating system on a Mac. Parallel is virtualization software and it is Mac only software. Of course we can use bootcamp on Mac to install Windows on our system, but using a bootcamp requires to shut the system down and boot from Windows partition. With Parallel you can run both operating systems at the same time side by side. In order to install it we need to go to [Parallel](https://www.parallels.com/) website. It is a paid software and requires a subscription. Students get 50% discount. After purchasing a license key it's time to download and install the software itself. The installation process is fairly easy. Now when we have it installed it's time to activate it. Go to Parallel Desktop menu and look for `Account & Licence`.

\
![image](/blog/assets/images/account&license.png)

\
Enter your activation key that you have purchased from the Parallel website

![image](/blog/assets/images/activationKey.png)

\
It will prompt you to login into your account or create a new one if your don't already have an account. After activation you have fully functional software. This is the main page after the installation where you need to install your Guest OS. Now when we have Parallel installed we need to download the OS iso file. In this case I am going to install [Ubuntu Linux](https://ubuntu.com/).

![image](/blog/assets/images/isoFile.png)

**Installing Ubuntu Linux**

Download the iso file for Ubuntu and save it on your desktop. Once you have it downloaded open Parallel and choose `"Instal Windows or another OS from a DVD or image file"`
click next, select the Linux iso file you saved earlier on your desktop and click continue. Ubuntu installer will start, make sure you choose `Install Ubuntu` from the list of options.

![image](/blog/assets/images/installUbuntu.png)

\
On the next page choose `Normal Installation` and click next

![image](/blog/assets/images/normalinstallation.png)

\
\
On the next page choose `Erase disk and install Ubuntu` and click `Install Now` this will erase the disk and repartition it. After installation is done it will ask you questions such as your location name, pc name, password etc... Enter all the required information and click `Continue`

![image](/blog/assets/images/chooseName.png)

\
Let the installation finalize and update all necessary components and after that's done - your installation is complete `Restart` your system. After the reboot Parallel Desktop will automatically install `Parallel Tools`- this is driver package for your Linux operating system in order for it to function correctly. After installing `Parallel Tools` reboot Linux for changes to take effect. And that's it now you have fully functional Ubuntu Linux running on your system side by side with your Mac OS. But the best part is Parallel Desktop offers `coherence mode`. Basically with `coherence mode` you let the operating system run in the background (in this case Ubuntu) and your don't interact with it at all, but you can use all the applications installed on Linux system as it would run straight from Mac OS. This is extremely useful if you need to run a program that can't be run on Mac OS directly.
