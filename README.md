A very lightweight container to PHP/Laravel/Lumen Development
==============================================

This container is based on [phusion/baseimage-docker](http://phusion.github.io/baseimage-docker/), that is a minimal Ubuntu base image modified for Docker-friendliness.
_Baseimage-docker **only consumes 6 MB RAM** and is much powerful than Busybox or Alpine. See why below._

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
docker run -p 80:80 --name container_name petronetto/php-nginx
```

Start the container with a Laravel/Lumen installation:
```bash
# Laravel
docker run -p 80:80 --name container_name petronetto/php-nginx:laravel

# Lumen
docker run -p 80:80 --name container_name petronetto/php-nginx:lumen
```

Using Composer:
```bash
docker run -it container_name composer <command>
```

Using Artisan:
```bash
docker run -it container_name php artisan <command>
```

In PHP installation, see the PHP info on http://localhost, or the static html page on http://localhost/test.html, on Laravel/Lumen in http://localhost


**NOTE**: If you're not running Docker Mac/Windows (which run Docker in a small virtualized layer), you may need to set permissions on the shared directories that Laravel needs to write to. The following will let Laravel write the storage and bootstrap directories:

```bash
# From your project directory
sudo chmod -R o+rw application/bootstrap application/storage
```

Maybe you also need change the project ownership:
```bash
# From your project directory
sudo chown -R $(whoami) application
```
