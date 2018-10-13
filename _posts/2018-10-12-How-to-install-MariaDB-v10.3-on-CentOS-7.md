---
layout: post
title:  "How to install MariaDB v10.3 on CentOS 7"
date:   2018-10-12 21:00:00 +0200
tags: linux database
author: "Daniel Rabanser "
comments: true
---
Hello there, *General Kenobi*. Just gonna share here how to install the latest MariaDB Server on CentOS.
<!--excerpt-->  
Since CentOS 7 comes with a dated (but still maintained) version of MariaDB, I just want to share how to install the latest and greatest version.

<br>

### Update your system
Get the latest updates for your server
```
[root@centos ~]# yum update
```

<br>

### Install using repository generator
Navigate to MariaDB's [repository generator](https://downloads.mariadb.org/mariadb/repositories/#mirror=nav) to really get the latest version  
Hit up vi or your preferred text editor
```
[root@centos ~]# vi /etc/yum.repos.d/MariaDB.repo
```
Insert the following and save the file
```
# MariaDB 10.3 CentOS repository list - created 2018-10-12 18:16 UTC
# http://downloads.mariadb.org/mariadb/repositories/
[mariadb]
name = MariaDB
baseurl = http://yum.mariadb.org/10.3/centos7-amd64
gpgkey=https://yum.mariadb.org/RPM-GPG-KEY-MariaDB
gpgcheck=1
```

<br>

### Install MariaDB Server
Now you'll be able to install MariaDB 10.3:
```
[root@centos ~]# yum install MariaDB-server MariaDB-client
```

<br>

### Start MariaDB / Enable autostart
What you want to do next is to start MariaDB and enable it to start automatically on boot time
```
[root@centos ~]# systemctl start mariadb
[root@centos ~]# systemctl enable mariadb
```

<br>

### Initial configuration
Now you'll need to run the installation script, it sets up the server  
Watch out if you want to manage the server using MySQL Workbench (you want to choose "n" for remote root login),  
I prefer to user phpMyAdmin so I'm turning it off though
```
[root@centos ~]# mysql_secure_installation
```
```
Set root password? [Y/n] y
Remove anonymous users? [Y/n] Y
Disallow root login remotely? [Y/n] Y
Remove test database and access to it? [Y/n] Y
Reload privilege tables now? [Y/n] Y
```

<br>
### Wrap up
That's it, that's all you need to do to get MariaDB up and running. 
You can verify the installed version of MariaDB by typing:
```
[root@centos ~]# mysql -V
```

<br>

If you want to know how to install and set up phpMyAdmin(will let you administer MariaDB via a Web Browser) I might do a post on that soon.
