---
layout: post
title:  "How to install CentOS 7"
date:   2018-07-05 19:00:00 +0200
tags: linux
author: "Daniel Rabanser "
comments: true
---
My first technical post, who would have thought I actually post here something, yeah me neither. So, if you are interested in how to install CentOS 7 read ahead.<!--excerpt-->


In this post you will learn how to install CentOS 7 and do some basic system setup.

<br>

### Start the installation
Test the media and install
![Install CentOS 7 - Test media and install](/assets/posts/2018-07-05-how-to-install-centos-7/1_InstallCentOS7TestMediaAndInstall.png)
Set your preferred language
![Install CentOS 7 - Set language](/assets/posts/2018-07-05-how-to-install-centos-7/2_InstallCentOS7SetLanguage.png)
Set your time zone
![Install CentOS 7 - Set time zone](/assets/posts/2018-07-05-how-to-install-centos-7/3_InstallCentOS7SetTimeZone.png)
Set your preferred keyboard layout
![Install CentOS 7 - Set keyboard layout](/assets/posts/2018-07-05-how-to-install-centos-7/4_InstallCentOS7SetKeyboardLayout.png)
Configure you disk, I prefer the manual way since all my Linux Server are webservers
![Install CentOS 7 - Configure partitioning](/assets/posts/2018-07-05-how-to-install-centos-7/5_InstallCentOS7ConfigurePartitioning1.png)
Create the basic partitioning
![Install CentOS 7 - Configure partitioning](/assets/posts/2018-07-05-how-to-install-centos-7/6_InstallCentOS7ConfigurePartitioning2.png)
If you wish to leave it to the defaults, proceed without making any further changes
![Install CentOS 7 - Apply default partitioning](/assets/posts/2018-07-05-how-to-install-centos-7/7_InstallCentOS7ApplyDefaultPartitioning.png)
If you want to set up dedicated partitions for /home and /var
![Install CentOS 7 - Apply custom partitioning](/assets/posts/2018-07-05-how-to-install-centos-7/8_InstallCentOS7ApplyCustomPartitioning.png)
Confirm the custom partitioning
![Install CentOS 7 - Confirm custom partitioning](/assets/posts/2018-07-05-how-to-install-centos-7/9_InstallCentOS7ConfirmCustomPartitioning.png)
Set your hostname and enable networking
![Install CentOS 7 - Set hostname](/assets/posts/2018-07-05-how-to-install-centos-7/10_InstallCentOS7SetHostname.png)
If you have a DHCP server on your network you should see something like this
![Install CentOS 7 - Enable networking](/assets/posts/2018-07-05-how-to-install-centos-7/11_InstallCentOS7EnableNetworking.png)
Start the installtion
![Install CentOS 7 - Start installation](/assets/posts/2018-07-05-how-to-install-centos-7/12_InstallCentOS7StartInstallation.png)
While we wait, set up the root password
![Install CentOS 7 - Wait](/assets/posts/2018-07-05-how-to-install-centos-7/13_InstallCentOS7Wait.png)
Reboot the system
![Install CentOS 7 - Reboot](/assets/posts/2018-07-05-how-to-install-centos-7/14_InstallCentOS7Reboot.png)
If you have forgotten the hostname/IP of your system log in and check it
![Install CentOS 7 - Connect and find IP](/assets/posts/2018-07-05-how-to-install-centos-7/15_ConnectToCentOS7AndFindIPAddress.png)



## Basic system setup
Proceed with a very basic system setup/configuration

<br>

### Update your system
First thing you want to do is update your system
```
[root@centos ~]# yum update
```
<br>

### Install drivers
If you are running CentOS 7 as a VM on Hyper-V you don't need to do anything :)  
If you are running on vmWare ESXi you will need to install vmWare Tools:
```
[root@centos ~]# yum install open-vm-tools
```
