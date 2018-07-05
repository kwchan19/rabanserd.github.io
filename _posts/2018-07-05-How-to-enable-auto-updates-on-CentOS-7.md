---
layout: post
title:  "How to enable auto updates on CentOS 7 w/ yum-cron"
date:   2018-07-05 20:00:00 +0200
tags: linux
author: "Daniel Rabanser "
comments: true
---
In this post you will learn how to enable automatic system updates for your CentOS 7 / RHEL 7 system.
<!--excerpt-->  

<br>

### Update your system
It might be a good idea to update your system before installing something. Kind of ironic isn't it? We'll do it anyway.
```
[root@centos ~]# yum update
```

<br>

### Install yum-cron
```
[root@centos ~]# yum install yum-cron
```

<br>

### Configure yum-cron
This will enable daily updates
```
[root@centos ~]# vi /etc/yum/yum-cron.conf
```
```
apply_updates = yes                  
```


This will enable hourly security updates
```
[root@centos ~]# vi /etc/yum/yum-cron-hourly.conf
```
```
update_cmd = security
update_messages = yes
download_updates = yes
apply_updates = yes
```

<br>

### Start yum-cron
Lastly start yum-cron and enable it to start automatically at boot time
```
[root@centos ~]# systemctl enable yum-cron
[root@centos ~]# systemctl start yum-cron
```