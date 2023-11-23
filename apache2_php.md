# ubuntu Apache2 PHP7.4:
1. [README](README.md)
5. [Install PHP 7.4](#php)\
5.1. [Install phpMyAdmin](#phpmyadmin)\
5.2. [phpMyAdmin secure](#phpmyadminS)\

Everyone use PHP 7.4 becasue is stable. In PHP 8 is changing a lot, we get new scurity updates and the fix a lot of bugs. So, many servers use PHP 7.4 and I will use the same version.

### 5. PHP7.4 Basic instalation and configuration [1]: <a name="php"></a>

Tutorial:\
[Install Older Version PHP](https://linux.how2shout.com/how-to-install-php-7-4-on-ubuntu-22-04-lts-jammy-linux/)

```sudo su``` - root permissions\
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
```<?php phpinfo() ?>```
Now is time to check configuretion:
```apt-get install php7.4-mysql```\
```apt-get install php7.4-mysqli```\
```apt-get install php7.4-mbstring```\
```apt-get install php7.4-pdo```\
```apt-get install php7.4-curl```\
```apt-get install php7.4-json```\
```apt-get install php7.4-zip```\


### phpMyAdmin install version 7.4: <a name="phpmyadmin"></a>

Tutorial: \
[phpMyAdmin 7.4 install](https://www.bennetrichter.de/en/tutorials/apache2-php7-mariadb-phpmyadmin/)\
[phpMyAdmin install and secure](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-20-04)

```sudo su```\
```cd /usr/share```\
[phpMyAdmin all versions](https://www.phpmyadmin.net/downloads/)\
```wget https://files.phpmyadmin.net/phpMyAdmin/5.2.1/phpMyAdmin-5.2.1-all-languages.zip```\
Check link like that to download from phpMyAdmin ftp server:\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/8de20b7f-cc54-466a-8a35-6efa9bd15901)\
After that:\
```unzip phpMyAdmin-5.2.1-all-languages.zip```\
If u dont have unzip use:\
```apt-get install unzip``` - unzip downloaded files\
```mv phpMyAdmin-5.2.1-all-languages phpmyadmin``` - change directory name on phpmyadmin\
```chmod -R 0755 phpmyadmin```\
```vi /etc/apache2/conf-available/phpmyadmin.conf```\
```
Alias /phpmyadmin /usr/share/phpmyadmin

<Directory /usr/share/phpmyadmin>
    Options SymLinksIfOwnerMatch
    DirectoryIndex index.php
    AllowOverride All
</Directory>

<Directory /usr/share/phpmyadmin/templates>
    Require all denied
</Directory>

<Directory /usr/share/phpmyadmin/libraries>
    Require all denied
</Directory>

<Directory /usr/share/phpmyadmin/setup/lib>
    Require all denied
</Directory>
```
```a2enconf phpmyadmin```\
```mkdir /usr/share/phpmyadmin/tmp/```\
```chown -R www-data:www-data /usr/share/phpmyadmin/tmp/```\
```systemctl reload apache2```\
 
### 5.2. Securing phpMyAdmin:  <a name="phpmyadminS"></a>

SOURCE: 
[1. Install Older Version PHP](https://linux.how2shout.com/how-to-install-php-7-4-on-ubuntu-22-04-lts-jammy-linux/)
