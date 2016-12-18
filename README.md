A very lightweight container to PHP/Laravel Development
==============================================

This container is based on [phusion/baseimage-docker](http://phusion.github.io/baseimage-docker/), that is a minimal Ubuntu base image modified for Docker-friendliness.
_Baseimage-docker **only consumes 6 MB RAM** and is much powerful than Busybox or Alpine._

This image contains:
- Ubuntu 14.04 (based on [phusion/baseimage-docker](http://phusion.github.io/baseimage-docker/))
- PHP-FPM 7.0
- Nginx 1.10
- NodeJS
- Git
- Composer

Usage
-----
Start the container:
```bash
# From your project folder
docker run -p 8080:80 --name php \
           -v $(pwd):/var/www/src \
           -w /var/www/src \
           -d petronetto/php-nginx
```

Start the container to Laravel development:
```bash
# From your project folder
docker run -p 8080:80 -it --name laravel \
           -v $(pwd):/var/www/src \
           -w /var/www/src \
           -d petronetto/php-nginx:laravel

# Creating a Larvel project from container
docker run -it --rm \
           -v $(pwd):/var/www/src \
           -w /var/www/src \
           petronetto/php-nginx:laravel \
           composer create-project laravel/laravel .
```

In PHP installation, see the PHP info on http://localhost:8080, or the static html page on http://localhost:8080/test.html


**NOTE**: If you're not running Docker Mac/Windows (which run Docker in a small virtualized layer), you may need to set permissions on the shared directories that Laravel needs to write to. The following will let Laravel write the storage and bootstrap directories:

```bash
# From your project folder
sudo chmod -R o+rw $(pwd)/bootstrap $(pwd)/storage
```

Maybe you also need change the project ownership if you using the container to create the new projects:
```bash
# From your project folder
sudo chown -R $(whoami) $(pwd)
```
