# ubuntu Apache2 CMS:
1. [README](README.md)
8. [CMS Install](#cms)

### 8. Install CMS:

```sudo su``` - root permission\
To check the app unzip, u can use this commend: ```unzip -v```. When u dont see version use commend below to install it:\
```apt install wget unzip``` - download and install unzip, which will be useful to install CMS\
```cd /var/www/cmssite.pl/public_html``` - move to /var/www/cmssite.pl/public_html, but u remember to reaplace it on your own domain\
To check your WordPress version, use this link [WordPress Versions](https://wordpress.org/download/releases/). It is important to have the latest versions, beacause developers continue to develop and improve the security of this application.\
```wget https://wordpress.org/wordpress-6.4.1.zip``` - download the Wordpress-6.4.1.zip\
```mv wordpress/ /var/www/<domain_name>``` - new directory with wordpress in main directory of website\
```rm wordpress-6.4.1.zip``` - remove installation files\
```cd ..``` - go back to previuse directory\
```chown www-data:www-data -R /var/www/html/wordpress/``` - change file permissions\
```chmod -R 755 /var/www/html/wordpress/``` - change file permissions\
```vi /etc/apache2/sites-available/cmssite.pl.conf``` - my domain is cmssite.pl u reaplace it on your own domain\
```
<VirtualHost *:80>
	Serveradmin admin@cmssite.pl
	ServerName cmssite.pl
	ServerAlias www.cmssite.pl
	DocumentRoot /var/www/cmssite.pl/wordpress/
	<Directory /var/www/mojastrona.pl/wordpress>
   		Options FollowSymLinks
   		AllowOverride All
  		Require all granted
	</Directory>
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
```a2ensite wordpress.conf``` - activation VirtualHost for domain cmssite.pl\
```systemctl reload apache2``` - reload apache2 server\

### Check on web browser:\
http://cmssite.pl\
Database configuration, when u don't have DB go to [MySQL](apache2_MySQL.md), then find "New User and DB" and follow the instructions. I used my DB like on image below.\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/6ebb9bc2-469b-4d11-bf6a-a05b25b24b57)
Create yourwebsite, admin and password to administrate website.\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/841428d3-b5fc-4a34-8e91-5681bbab77e0)
Log in.\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/0d41bab2-a468-49b7-9f53-4e78529b7f5e)
Welcome on WordPress Dashboard.\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/260e2ec1-620d-430b-9b4e-92e38684b974)


SOURCE:
[Wordpress Install](https://linux.how2shout.com/how-to-install-wordpress-on-ubuntu-22-04-lts-server/)
