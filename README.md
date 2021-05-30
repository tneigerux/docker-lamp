## Docker with LAMP stack based on Alpine Linux

This docker contain a LAMP stack installed from scratch

## Installation
### Grab from docker hub
```
docker pull iopenservices/docker-lamp
```

### Run you own image
```  
git clone https://github.com/tneigerux/docker-lamp && cd docker-lamp/
```

### Build the image
```
docker build -t iopenservices/docker-lamp .
```

### Run it

Set DOCROOT-PATH equal to /path/to/public_html (no trailing slash)

e.g. ```/Users/iopen/Development/example-com/public/```

```
docker run -d -v <DOCROOT-PATH>:/var/www/localhost/htdocs/ -e MYSQL_ROOT_PASSWORD=password -p 80:80 -p 3306:3306 --name www-example-local iopenservices/docker-lamp
```

### Connect to MariaDB
To use this you need to install mysql/mariadb cli client
```
mysql -uroot -ppassword -h 127.0.0.1
```

### PhpMyAdmin

If you want to use phpMyAdmin use the branch called: **phpmyadmin-feature**


## Troubleshooting

### Forbidden error 403 
```
sudo chmod -Rf 755 /path/to/project
``` 

### Error activating InnoDB
If you get errors about activating InnoDB and you are on Windows or Mac, you
may be encountering [this
issue](https://github.com/docker-library/mariadb/issues/95) with using
host-mapped volumes for MariaDB. Work-around is to use a named volume
(persistent but not mapped), or [add/overwrite mysql config](https://github.com/docker-library/mariadb/issues/95#issuecomment-391587301) before entry.

### Missing libs
Please let me know or create a pull request

## Repos
https://hub.docker.com/r/j1cs/alpine-lamp  
https://github.com/j1cs/alpine-lamp
