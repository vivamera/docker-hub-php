# VIVAMERA php docker image

[![Build Status](https://travis-ci.com/vivamera/docker-hub-php.svg?branch=master)](https://travis-ci.com/vivamera/docker-hub-php)
[![Codacy Badge](https://api.codacy.com/project/badge/Grade/f4159283450f40bbbc0ea8b3c67bf6a4)](https://www.codacy.com/app/vivamera/docker-hub-php?utm_source=github.com&utm_medium=referral&utm_content=vivamera/docker-hub-php&utm_campaign=Badge_Grade)

This repository provides a docker image for `PHP` with is based upon `php alpine`.

This docker image provides the following extensions:
- bcmath
- gd
- intl
- pdo_pgsql
- redis
- xdebug

And provides binaries for image optimizations:
- jpegoptim (https://github.com/tjko/jpegoptim)
- optipng (https://downloads.sourceforge.net/project/optipng/OptiPNG)
- pngquant (http://pngquant.org)
- gifsicle (https://github.com/kohler/gifsicle)

And it also provides configurations for:
- [php](7.2/etc/php/conf.d)
- [openssl](7.2/etc/ssl)

## Set Up
1. To use Docker images you require docker
    * macOS: [Download Docker for Mac](https://www.docker.com/docker-mac)
    * Windows: [Download Docker for Windows](https://www.docker.com/docker-windows)
2. Install Docker and [Docker Toolbox](https://www.docker.com/toolbox)

## Build

To build the image run the following command:

```bash
$ docker build \
    --tag vivamera/php \
    7.2
```

## Usage

To use the image run the following command:

```bash
$ docker run \
    --rm \
    --interactive \
    --tty \
    --volume "${PWD}":/app \
    vivamera/php
```

To use the image with xdebug enabled, add the following option `-d zend_extension=xdebug.so`
