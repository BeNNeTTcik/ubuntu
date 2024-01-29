apache2_ssl

sudo a2enmod ssl


```
< VirtualHost *:80 >
ServerName www.yourdomain.com
Redirect permanent /secure https://yourdomain.com/secure
< /VirtualHost >

< VirtualHost _default_:443 >
ServerName www.yourdomain.com
DocumentRoot /usr/local/apache2/htdocs
SSLEngine On
...
< /VirtualHost >
```
