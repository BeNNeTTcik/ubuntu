1. Install PHP

Everyone use PHP 7.4 becasue is stable. In PHP 8 is changing a lot, we get new scurity updates and the fix a lot of bugs. So, many servers use PHP 7.4 and I will use the same version.

## Basic instalation and configuration:

Tutorial: [Install Older Version PHP](https://linux.how2shout.com/how-to-install-php-7-4-on-ubuntu-22-04-lts-jammy-linux/)

```sudo su```\
```apt install software-properties-common```
```add-apt-repository ppa:ondrej/php -y```
```apt-get install php7.4```\
```cd /etc/apache2/mods-enabled```\
```vi dir.conf```\
```
<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```
```systemctl restart apache2```
I used ["userdir"](apache2_mods.md) to create space for test php. In "/etc/asia/public_html" I create index.php and configuretion looks like:
```<?php phpinfo() ?>```
Now is time to check configuretion:




```apt-get install php-mysql```\
```apt-get install php-mysqli```\
```apt-get install php-mbstring```\
```apt-get install php-pdo```\
```apt-get install php-curl```\
```apt-get install php-json```\
```apt-get install php-zip```\
