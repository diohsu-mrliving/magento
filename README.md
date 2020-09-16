# magento

## Time zone and ntp
```
apt-get update
dpkg-reconfigure tzdata
apt-get install ntp
```

## Nginx
```
apt-get update
apt-get -y install nginx
```

### Nginx config
* `/etc/nginx/sites-available/default`

Uncomment the partial commands of the PHP section as below.

```
# pass PHP scripts to FastCGI server                                                                       
#                                                                                                          
location ~ \.php$ {                                                                                        
        include snippets/fastcgi-php.conf;                                                                 

        # With php-fpm (or other unix sockets):                                                            
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;                                                    
#       # With php-cgi (or other tcp sockets):                                                             
#       fastcgi_pass 127.0.0.1:9000;                                                                       
}   
```

## PHP & modules (extensions)
```
apt-get update
apt-get -y install php7.4-fpm php7.4-cli
```

```
apt-get install php7.4-pdo php7.4-mysqlnd php7.4-opcache php7.4-xml php7.4-gd php7.4-devel php7.4-mysql php7.4-intl php7.4-mbstring php7.4-bcmath php7.4-json php7.4-iconv php7.4-soap
```

## Check PHP/Nginx services
### Restart services
```
systemctl restart php7.4-fpm.service
systemctl restart nginx.service 
```

### Verify PHP is installed
* `/var/www/html/phpinfo.php`
```
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
?>
```

## Elasticsearch
### [OpenJDK](https://openjdk.java.net/)
* [Support Matrix](https://www.elastic.co/support/matrix#matrix_jvm)
```
apt-get update
apt-get install openjdk-11-jdk
```

### [download 7.6.2](https://www.elastic.co/downloads/past-releases/elasticsearch-7-6-2)

* open `http://${HOST}/phpinfo.php` with a browser 

## [Install the Magento with the compressed archive](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/zip_install.html)
* [get the Magento archives](https://magento.com/tech-resources/download)
  * under **Archive (zip/tar)** section


## Composer 
### [Command-line installation](https://getcomposer.org/download/)
```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '795f976fe0ebd8b75f26a6dd68f78fd3453ce79f32ecb33e7fd087d39bfeb978342fb73ac986cd4f54edd0dc902601dc') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```


## Reference
* [magento helpful resources](https://devdocs.magento.com/guides/v2.4/install-gde/install-resources-parent.html)
