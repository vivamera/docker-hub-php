FROM php:7.2-alpine

LABEL maintainer="VIVAMERA"

ENV XDEBUG_VERSION="2.6.0"
ENV JPEGOPTIM_URL="https://github.com/tjko/jpegoptim/archive/RELEASE.1.4.4.tar.gz"
ENV OPTIPNG_URL="https://downloads.sourceforge.net/project/optipng/OptiPNG/optipng-0.7.7/optipng-0.7.7.tar.gz"
ENV PNGQUANT_URL="http://pngquant.org/pngquant-2.11.4-src.tar.gz"
ENV GIFSICLE_URL="https://github.com/kohler/gifsicle/archive/v1.90.tar.gz"

RUN apk add --no-cache --virtual .build-deps \
    ${PHPIZE_DEPS} \
    automake \
    bash

# Install persistent dependencies
RUN apk add --no-cache --virtual .persistent-deps \
    icu-dev \
    postgresql-dev \
    libjpeg-turbo-dev \
    libpng-dev

# Build
RUN set -xe \
    && docker-php-ext-install \
        bcmath \
        gd \
        intl \
        pdo_pgsql \
    && pecl install \
        redis \
        xdebug-"${XDEBUG_VERSION}" \
    && docker-php-ext-enable \
        redis

RUN set -xe \
    && mkdir -p /usr/src /tmp/jpegoptim \
    && wget -O /usr/src/jpegoptim.tar.gz "${JPEGOPTIM_URL}" \
    && tar -xzf /usr/src/jpegoptim.tar.gz -C /tmp/jpegoptim --strip-components 1 \
    && cd /tmp/jpegoptim \
    && ./configure \
    && make \
    && make strip \
    && make install \
    && cd /tmp \
    && rm -f /usr/src/jpegoptim.tar.gz \
    && rm -rf /tmp/jpegoptim

RUN set -xe \
    && mkdir -p /usr/src /tmp/optipng \
    && wget -O /usr/src/optipng.tar.gz "${OPTIPNG_URL}" \
    && tar -xzf /usr/src/optipng.tar.gz -C /tmp/optipng --strip-components 1 \
    && cd /tmp/optipng \
    && ./configure \
    && make \
    && make install \
    && cd /tmp \
    && rm -f /usr/src/optipng.tar.gz \
    && rm -rf /tmp/optipng

RUN set -xe \
    && mkdir -p /usr/src /tmp/pngquant \
    && wget -O /usr/src/pngquant.tar.gz "${PNGQUANT_URL}" \
    && tar -xzf /usr/src/pngquant.tar.gz -C /tmp/pngquant --strip-components 1 \
    && cd /tmp/pngquant \
    && ./configure \
    && make \
    && make install \
    && cd /tmp \
    && rm -f /usr/src/pngquant.tar.gz \
    && rm -rf /tmp/pngquant

RUN set -xe \
    && mkdir -p /usr/src /tmp/gifsicle \
    && wget -O /usr/src/gifsicle.tar.gz "${GIFSICLE_URL}" \
    && tar -xzf /usr/src/gifsicle.tar.gz -C /tmp/gifsicle --strip-components 1 \
    && cd /tmp/gifsicle \
    && autoreconf -i \
    && ./configure \
    && make \
    && make install \
    && cd /tmp \
    && rm -f /usr/src/gifsicle.tar.gz \
    && rm -rf /tmp/gifsicle

RUN apk del .build-deps

COPY etc/php/conf.d/* "${PHP_INI_DIR}"/conf.d/
COPY etc/ssl/openssl.cnf /etc/ssl/

WORKDIR /app

ENTRYPOINT [ "php" ]

CMD [ "-a" ]
