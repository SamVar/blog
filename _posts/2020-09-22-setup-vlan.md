---
layout: post
author: "Samvel Vardanyan"
title: "VLAN Setup"
date: 2020-09-22 12:00:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

**What is a VLAN?**

VLAN is a broadcast domain created by switches. Normally, it is a router creating that broadcast domain. With VLAN’s, a switch can create the broadcast domain. So in other words we can have all the hosts physically connected to one switch and configure the switch to have more than one network. Another option that we can use with VLANs is to combine more than one networks and make it as one big logical network.

**Configuration Overview**

There are 3 steps we need to take to successfully setup a VLAN.

1. **Add the VLANs**\
   Most switches have a means of defining a list of configured VLANs, and they must be added before they can be configured on any ports.

2. **Configure the trunk port**\
   The port to which the a firewall or a router will be connected must be configured as a trunk port, tagging all possible VLANs on the interface.

3. **Configure the access ports**\
   Configure ports for internal hosts as access ports on the desired VLANs, with untagged VLANs.

\
**Enable VLAN Support**

In order for us to setup VLAN correctly we need to enable VLAN support. So we login to our switch:

1. Choose **Switch configuration**

2. Choose **Advanced Features**

3. Choose **VLAN Menu**

4. Choose **VLAN Support**

5. Set **Enable VLANs** to **Yes**

Restart the switch to apply the changes.

\
**Add VLANs**

First we need to create VLANs in order to assign to ports. Go to **Switch Configuration** menu:

1. Choose **Switch configuration**

2. Choose **Advanced Features**

3. Choose **VLAN Menu**

4. Choose **VLAN Names**

5. Choose **Add**

6. Enter the **VLAN ID**

7. Enter the **name**

8. Choose **Save**

9. Repeat the steps for any remaining VLANs

\
**Configure the Trunk Ports**

Next, we are going to configure the trunk port for the firewall as well as any trunk ports going to other switches containing multiple VLANs.

1. Choose **Switch configuration**

2. Choose **VLAN Menu**

3. Choose **VLAN Port Assignment**

4. Choose **Edit**

5. Find the port to assign

6. Press **space** on Default VLAN until it shows **No**

7. Move over to the column for each of the VLANs on this trunk port, and Press **space** until it shows **Tagged**.

\
**Assigning Access Ports to VLANs**

1. Choose **Switch configuration**

2. Choose **VLAN Menu**

3. Choose **VLAN Port Assignment**

4. Choose **Edit**

5. Find the port to assign

6. Press **space** on **Default VLAN** until it shows **No**

7. Move over to the column for the VLAN to which this port will be assigned

8. Press **space** until it shows **Untagged**.

\
This example was for **HP ProCurve** switch which supports 802.1q trunking, so no configuration is needed for encapsulation. Same configuration can be done for different type of switches even though the process can be slightly different.
