# PHP
[![Build Status](https://circleci.com/gh/vivamera/docker-hub-php.svg?style=svg)](https://circleci.com/gh/vivamera/docker-hub-php)

This is a image for `PHP` witch is based upon `alpine php`.

This image provides the following extensions:
- bcmath
- gd
- intl
- pdo_pgsql
- redis
- grpc
- xdebug

The following binaries for image optimizations will be provided:
- jpegoptim (https://github.com/tjko/jpegoptim)
- optipng (https://downloads.sourceforge.net/project/optipng/OptiPNG)
- pngquant (http://pngquant.org)
- gifsicle (https://github.com/kohler/gifsicle)

## Supported tags and respective Dockerfile links
* `7.2`, `latest` [(7.2/Dockerfile)](https://github.com/vivamera/docker-hub-php/blob/master/7.2/Dockerfile)

## How to use this image
For PHP projects run through the command line interface (CLI), you can run the following.

```bash
$ docker run \
    --rm \
    --interactive \
    --tty \
    --workdir /app \
    --volume "$(pwd)":/app \
    vivamera/php my-php-script.php
```

To use the image with **xdebug** enabled, add the following `php` option `-d zend_extension=xdebug.so`, as example run the following.

```bash
$ docker run \
    --rm \
    --interactive \
    --tty \
    --workdir /app \
    --volume "$(pwd)":/app \
    vivamera/php -d zend_extension=xdebug.so my-php-script.php
```

## Quick reference
* **Where to get help:**
[the Docker Community Forums](https://forums.docker.com), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

* **Where to file issues:**
https://github.com/vivamera/docker-hub-php/issues

* **Maintained by:**
[The VIVAMERA Team](https://github.com/vivamera)

* **Source of this description:**
[Repository README.md](https://github.com/vivamera/docker-hub-php/blob/master/README.md)
