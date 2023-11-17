# ubuntu Apache2 Modules:\
1. [Modules](#modules)\
1.1. [userdir](#userdir)\
1.2. [rewrite](#rewrite)\
1.3. [ssl](#ssl)

## 1. Additional modules: <a name="modules"></a>

| Module   | Installion script       | Short informations |
|---------|----------------------|-------------------|
| [userdir](#userdir) | sudo a2enmod userdir |      allowing multiple users to host content within the same origin, like http//domain.xyz/~user             |
| [rewrite](#rewrite) | sudo a2enmod rewrite |     can be used to redirect one URL to another URL; allows manipulation of the entire URL address     | 
| [ssl](#ssl)     | sudo a2enmod ssl     |           works on OpenSSL engine and provide the cryptography        |

### Userdir configuration: <a name="userdir"></a>

Before configuration we should have user on the VM. To add user use this commend ```sudo adduser <name of the user>```.\
Configuration userdir:\
```su $<name of created user>``` - we change root client on user client.\
```mkdir ./public_html && chmod 755 ./public_html``` - in home catalog we create a new folder and change folder permissions on 755.\
```exit``` - leave from user client to root client.\
```service apache2 restart``` - restart apache2 services all the time after changes.\
```cd /home/<name of the user>/public_html``` - change directory on public_html, because we need create a new file "index.html".\
```vi index.html``` - u can replace "vi" on "nano" and create a file.\
Inside file "index.html" write simple website to check configuration:\
```
<html>
 <body>
  <title> Mateusz Swiat </title>
 </body>
</html>
```

After all u should open website after ip or domain on your web browser:\
In URL use IP to connect:\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/0fcc56a5-c390-4844-a2b8-b119465f2cf9)\
In URL use domain name to connect:\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/d9fa587a-db84-4efd-bc19-963453cc256f)\

### Rewrite configuration: <a name="rewrite"></a>

Good tutorial *[How To Rewrite URLs with mod_rewrite for Apache](https://www.digitalocean.com/community/tutorials/how-to-rewrite-urls-with-mod_rewrite-for-apache-on-ubuntu-16-04)*

In directory: "/etc/apache2/sites-avaliable/" we need modify a file "mojastrona.pl.conf" by "vi/nano":\
```
...
DocummentRoot /var/www/mojastrona.pl/public_html/
<Directory /var/www/mojastrona.pl/public_html>
   Options Indexes FollowSymLinks MultiViews
   AllowOverride All
   Require all granted
</Directory>
...
```
```vi /var/www/mojastrona.pl/public_html/.htaccess``` - create new file which will attend in mod_rewrite\ 
Add this inside ".htaccess":\
```
RewriteEngine on
RewriteRule ^index$ index.html [NC]
```
Now try in URL write: "http://mojastrona.pl/index" this URL will be rewrite to "http://mojastrona.pl/index.html". It means mod_rewrite works.

### SSL configuration: <a name="ssl"></a>
Tutorials:\
![How configure 2 domains](https://www.youtube.com/watch?v=IH9MmUQiOI4)\
![SSL Configuration](https://www.youtube.com/watch?v=rgBY6phztlk)\

Commmends to configure 2 domains (http and https):\
```sudo su``` - root permissions\
```mkdir -p /var/www/example.com/public_html``` - create first domain directory\
```mkdir -p /var/www/test.com/public_html``` - create secound ssl domain directory\
```chmod -R 755 /var/www``` - "R" all files and directory got permission 755\
```cd /var/www``` - move to /var/www\
```vi ./example.com/public_html/index.html``` - create website for domain example.com\
```<h1>Example.com ez</h1>``` - website\
```vi ./test.com/public_html/index.html```  - create website for domain test.com\
```<h1>test.com ez</h1>``` - website\
```cd /etc/apache2/sites-avaliable/``` - move to /etc/apache2/sites-avaliable\
```cp ./000-default.conf example.com.conf``` - copy 000-default.conf to example.com.conf\
```cp ./default-ssl.conf test.com.conf```- copy default-ssl.conf to test.com.conf\
```vi example.com.conf``` - edit VirtualHost\
Check file in repositories -> example.com.conf\
```vi test.com.conf```\
Check file in repositories -> test.com.conf\
```a2ensite example.com.conf``` - activation VirtualHost for domain example.com\
```a2ensite test.com.conf``` - activation VirtualHost for domain test.com\
```a2dissite 000-default.conf``` - deactivation VirtualHost\
```service apache2 restart``` - restart apache2\
```cd ..``` - go back to the previous directory \
```mkdir ssl``` - create ssl directory\
```openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/test.com.key -out /etc/apache2/ssl/test.com.crt``` - create certificate\
Rest paramiters are without matter beside COMMON NAME: f.g. PL, Pomeranian, Gdynia, MyOrg, MyOrg, test.com, webmaster@server.local\
Time to check on your web browser: http://example.com and https://test.com\

Check configuration:\
![image](https://github.com/BeNNeTTcik/ubuntu_apache/assets/42866234/3627b289-4863-4173-9c3c-ef2b86418c80)
