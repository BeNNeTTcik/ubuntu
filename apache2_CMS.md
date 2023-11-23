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
