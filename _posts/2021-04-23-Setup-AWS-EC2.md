---
layout: post
author: "Samvel Vardanyan"
title: "Setting Up AWS EC2"
date: 2021-04-23 12:40:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

Because we are working on group project for this class which involves creating our infrastructure on AWS, I decided for this weekly blog I will talk about how to create AWS EC2 instance. It's pretty straight forward task. All we need is AWS free tier account and some basic knowledge of AWS and EC2 instances. That's on mind let's create our first EC2 instance on AWS. 

\
**EC2 Server Setup**

Once we log in to the console, you will see a screen like below:

![image](/blog/assets/images/aws-console.png)

\
On the top-right corner we can see the region selector. AWS provides services different regions across the world, and it is still growing. Choose a region as your choice, or leave it to US East (N. Virginia) as default. Different regions may vary in pricing. Here in the `service` tab we can choose `EC2`. In EC2 management console we can start the launching process by pressing `Launch Instance`:

\
![image](/blog/assets/images/launch-instance.png)

\
Choose a machine image (AMI for short) to begin. This is the operating system that will run on our machine. I will choose `Amazon Linux` after doing so we need to select an instance type. I will start with t2.micro, because we can get 750 hours of free usage every month with this instance for the first year. Note this is valid only the first year from the date we sign up, and only for the t2.micro instance. 

\
![image](/blog/assets/images/instance-type.png)

\
Once we click `Review and Launch` we can configure all the detailed settings on this page, but we are going to leave everything default and click `Launch`. Finally, to access a remote server, we need an identity. AWS will prompt us to choose an SSH key pair, as in the image below. Download the privacy key file and click the launch button. And yes, we are done; a new virtual server is being configured and will be ready in a few minutes.

\
![image](/blog/assets/images/aws-key-pair.png)

\
Once the instance is ready, we may ssh into the system as default user ec2-user, with our privacy key.



