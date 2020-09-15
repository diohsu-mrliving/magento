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

### 
* `/var/www/html/phpinfo.php`
```
<?php
// Show all information, defaults to INFO_ALL
phpinfo();
?>
```


## Reference
* [magento helpful resources](https://devdocs.magento.com/guides/v2.4/install-gde/install-resources-parent.html)
