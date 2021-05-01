---
layout: post
author: "Samvel Vardanyan"
title: "AWS RDS Instance"
date: 2021-04-30 20:20:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**Introduction**

Amazon RDS (Relational Database Service) is a web service which helps in setting-up, operating and scaling the relational database in the cloud. The service is cost-efficient and can be used by industries for database administration tasks. In this post, we will look at the detailed steps involved in creating an RDS database (MySQL) instance that helps maintain the data which is used by a web application.

**Steps to Create an RDS Instance**

1. Sign into AWS Management Console.  
2. Open the RDS console.  
3. In the upper-right corner, choose the region where you wish to create your instance.  
4. In the navigation pane, click on ‘Databases’.  
5. Click on ‘Create database’.  
6. Make sure ‘Standard create’ is chosen, then click on MySQL (or the database which you wish to create an RDS database instance).  

\
![image](/blog/assets/images/database.png)

{:start="7"}
7. In the ‘Templates’ tab, click on the ‘Dev/Test’ option.  
8. In the ‘Setting’ tab, set the following values:

- DB instance identifier
- Master username
- Auto Generate a password
- Master password
- Confirm password

{:start="9"}
9. In the ‘DB instance size’ option we give a value for the following variables:

- DB instance performance types
- DB instance class

{:start="10"}
10. In the ‘Storage’ and ‘Availability & durability’ section, leave the default values as is.
11. In the ‘Connectivity’ section, click on the ‘Additional connectivity configuration’ and set the below values in it:

- Virtual Private Cloud (VPC)
- Subnet group
- Publicly accessible- No
- VPC security groups
- Availability zone- No preference
- Database port- 3306

{:start="12"}
12. Click on the ‘Additional configuration’tab, and provide a name for the ‘Initial database name’ variable. The default settings for other options need to be kept the same.
13. Now click on ‘Create database’.

