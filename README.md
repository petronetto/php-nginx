A very lightweight container to PHP Development
==============================================

This container is based on [phusion/baseimage-docker](http://phusion.github.io/baseimage-docker/), that is a minimal Ubuntu base image modified for Docker-friendliness.
_Baseimage-docker **only consumes 6 MB RAM** and is much powerful than Busybox or Alpine. See why below._

This image contains:
- Ubuntu (based on [phusion/baseimage-docker](http://phusion.github.io/baseimage-docker/))
- PHP-FPM 7.0
- Nginx 1.10
- NodeJS
- Git
- Composer

Usage
-----
Start the Docker containers:

`sudo docker run -p 80:80 --name container_name petronetto/php-nginx`

Using Composer:
```
# Create a Laravel application
docker run -it container_name composer create-project laravel/laravel application
```

See the PHP info on http://localhost, or the static html page on http://localhost/test.html
