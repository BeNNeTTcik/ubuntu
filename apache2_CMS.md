# ubuntu Apache2 CMS:
1. [README](README.md)
8. [CMS Install](#cms)

### 8. Install CMS:

```sudo su``` - root permission\
To check the app unzip, u can use this commend: ```unzip -v```. When u dont see version use commend below to install it:\
```apt install wget unzip``` - download and install unzip, which will be useful to install CMS\
```cd /var/www/<domain_name>/public_html```
To check the version of wordpress use this link [Wordpress Releases](https://wordpress.org/download/releases/)
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

