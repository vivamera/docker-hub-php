# PHP
[![Build Status](https://travis-ci.com/vivamera/docker-hub-php.svg?branch=master)](https://travis-ci.com/vivamera/docker-hub-php) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/f4159283450f40bbbc0ea8b3c67bf6a4)](https://www.codacy.com/app/vivamera/docker-hub-php?utm_source=github.com&utm_medium=referral&utm_content=vivamera/docker-hub-php&utm_campaign=Badge_Grade) 

This is a image for `PHP` witch is based upon `php alpine`.

This image provides the following extensions:
- bcmath
- gd
- intl
- pdo_pgsql
- redis
- xdebug

The following binaries for image optimizations will be provided:
- jpegoptim (https://github.com/tjko/jpegoptim)
- optipng (https://downloads.sourceforge.net/project/optipng/OptiPNG)
- pngquant (http://pngquant.org)
- gifsicle (https://github.com/kohler/gifsicle)

The image provides configuration for:
- [php](https://github.com/vivamera/docker-hub-php/tree/master/7.2/etc/php)
- [openssl](https://github.com/vivamera/docker-hub-php/tree/master/7.2/etc/ssl)

## Supported tags and respective Dockerfile links
* `7.2`, `latest` [(7.2/Dockerfile)](https://github.com/vivamera/docker-hub-php/blob/master/7.2/Dockerfile)

## How to use this image
For PHP projects run through the command line interface (CLI), you can do the following.

```bash 
$ docker run \
    --rm \
    --interactive \
    --tty \
    --volume "$(pwd)":/app \
    vivamera/php my-php-script.php
```

To use the image with xdebug enabled, add the following option `-d zend_extension=xdebug.so`

## Quick reference
* **Where to get help:**
[the Docker Community Forums](https://forums.docker.com), [the Docker Community Slack](https://blog.docker.com/2016/11/introducing-docker-community-directory-docker-community-slack), or [Stack Overflow](https://stackoverflow.com/search?tab=newest&q=docker)

* **Where to file issues:**
https://github.com/vivamera/docker-hub-php/issues

* **Maintained by:**
[The VIVAMERA Team](https://github.com/vivamera)

* **Source of this description:**
[Repository README.md](https://github.com/vivamera/docker-hub-php/blob/master/README.md)
