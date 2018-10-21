---
layout: post
title:  "How to install Let's Encrypt certificates for Apache on CentOS 7 using Certbot"
date:   2018-10-21 21:30:00 +0100
tags: linux web
author: "Daniel Rabanser "
comments: true
---
In my previous post I went through serving websites with Apache, now I want to secure those sites with a free Let's Encrypt certificate
<!--excerpt-->  using the certbot client.

<br>

### Update your system
Get the latest updates for your server
```
[root@centos ~]# yum update
```

<br>

### Add the EPEL repo to your system
In order to install the certbot client on CentOS 7 you'll need to have the EPEL repository installed.
```
[root@centos ~]# yum install epel-release
```

<br>

### Install certbot
Navigate to certbot's [configurator](https://certbot.eff.org/lets-encrypt) to select your distro. I'm using Apache on CentOS 7.  
This command below will install the certbot client and it's needed dependencies.
```
[root@centos ~]# yum install python2-certbot-apache
```

<br>

### Generate certificates / keys


```
[root@centos ~]# certbot --apache
```
When you run this command for the first time you will be asked for your renewal email, Terms of Service Agreement and if you are willing to share your E-Mail with the EFF:
```
Enter email address (used for urgent renewal and security notices) (Enter 'c' to
cancel): daniel@rabanser.tech
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.2-November-15-2017.pdf. You must
agree in order to register with the ACME server at
https://acme-v02.api.letsencrypt.org/directory
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(A)gree/(C)ancel: A

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing to share your email address with the Electronic Frontier
Foundation, a founding partner of the Let's Encrypt project and the non-profit
organization that develops Certbot? We'd like to send you email about our work
encrypting the web, EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: N
```
Then you can proceed with your certificate request:
```
Which names would you like to activate HTTPS for?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: simple-demo.rabanser.tech
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel): 1

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2
Redirecting vhost in /etc/httpd/conf.d/simple-demo.rabanser.tech.conf to ssl vhost in /etc/httpd/conf.d/simple-demo.rabanser.tech-le-ssl.conf

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations! You have successfully enabled https://simple-demo.rabanser.tech
```

<details>
 <summary>Whole output</summary>
<div markdown="1">
```
Enter email address (used for urgent renewal and security notices) (Enter 'c' to
cancel): daniel@rabanser.tech
Starting new HTTPS connection (1): acme-v02.api.letsencrypt.org

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Please read the Terms of Service at
https://letsencrypt.org/documents/LE-SA-v1.2-November-15-2017.pdf. You must
agree in order to register with the ACME server at
https://acme-v02.api.letsencrypt.org/directory
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(A)gree/(C)ancel: A

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Would you be willing to share your email address with the Electronic Frontier
Foundation, a founding partner of the Let's Encrypt project and the non-profit
organization that develops Certbot? We'd like to send you email about our work
encrypting the web, EFF news, campaigns, and ways to support digital freedom.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
(Y)es/(N)o: N
Which names would you like to activate HTTPS for?
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: simple-demo.rabanser.tech
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate numbers separated by commas and/or spaces, or leave input
blank to select all options shown (Enter 'c' to cancel): 1
Obtaining a new certificate
Performing the following challenges:
http-01 challenge for simple-demo.rabanser.tech
Waiting for verification...
Cleaning up challenges
Created an SSL vhost at /etc/httpd/conf.d/simple-demo.rabanser.tech-le-ssl.conf
Deploying Certificate to VirtualHost /etc/httpd/conf.d/simple-demo.rabanser.tech-le-ssl.conf

Please choose whether or not to redirect HTTP traffic to HTTPS, removing HTTP access.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
1: No redirect - Make no further changes to the webserver configuration.
2: Redirect - Make all requests redirect to secure HTTPS access. Choose this for
new sites, or if you're confident your site works on HTTPS. You can undo this
change by editing your web server's configuration.
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Select the appropriate number [1-2] then [enter] (press 'c' to cancel): 2
Redirecting vhost in /etc/httpd/conf.d/simple-demo.rabanser.tech.conf to ssl vhost in /etc/httpd/conf.d/simple-demo.rabanser.tech-le-ssl.conf

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -
Congratulations! You have successfully enabled https://simple-demo.rabanser.tech

You should test your configuration at:
https://www.ssllabs.com/ssltest/analyze.html?d=simple-demo.rabanser.tech
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - -

IMPORTANT NOTES:
 - Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/simple-demo.rabanser.tech/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/simple-demo.rabanser.tech/privkey.pem
   Your cert will expire on 2019-01-19. To obtain a new or tweaked
   version of this certificate in the future, simply run certbot again
   with the "certonly" option. To non-interactively renew *all* of
   your certificates, run "certbot renew"
 - If you like Certbot, please consider supporting our work by:

   Donating to ISRG / Let's Encrypt:   https://letsencrypt.org/donate
   Donating to EFF:                    https://eff.org/donate-le

```
</div>
</details>

<br>
You can now navigate to your site and check your new certificate.
![Site](/assets/posts/2018-10-21-how-to-install-lets-encrypt-certificates-for-apache-on-centOS-7-using-certbot/1_Site.png)

<br>

### Renew your certificates

Manual renewal:
```
[root@centos ~]# certbot renew
```

<br>

Since Let's Encrypt Certificates have a validity period of 90 days, you might want to set up a cron-job which renews the certificates for you

Cron-job:
```
[root@centos ~]# crontab -e
```
Insert the following for a cron job which runs every day at 6 AM
```
0 6 * * * certbot renew >/dev/null 2>&1
```