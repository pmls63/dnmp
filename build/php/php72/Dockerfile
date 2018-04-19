FROM php:7.2.4-fpm-alpine3.7

MAINTAINER pmls63 1083239138@qq.com

# setup remote php packagages
ADD https://php.codecasts.rocks/php-alpine.rsa.pub /etc/apk/keys/php-alpine.rsa.pub

RUN set -xe \
    && echo "https://php.codecasts.rocks/v3.7/php-7.2" >> /etc/apk/repositories \
    && echo "@php https://php.codecasts.rocks/v3.7/php-7.2" >> /etc/apk/repositories \
    && apk add --update --no-cache \
    ca-certificates \
    curl \
    openssh-client \
    libmemcached-libs \
    libevent \
    libssl1.0 \
    musl \
    yaml \
    php7 \
    php7-apcu@php \
    php7-bcmath \
    php7-ctype \
    php7-curl \
    php7-dom \
    php7-iconv \
    php7-intl \
    php7-json \
    php7-openssl \
    php7-opcache \
    php7-mbstring \
    php7-memcached \
    php7-mysqlnd \
    php7-mysqli \
    php7-pcntl \
    php7-pgsql \
    php7-pdo_mysql \
    php7-pdo_pgsql \
    php7-pdo_sqlite \
    php7-phar \
    php7-posix \
    php7-session \
    php7-soap \
    php7-sockets \
    php7-sodium \
    php7-xml \
    php7-xmlreader \
    php7-zip \
    php7-zlib \
    && apk add --no-cache --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/ --allow-untrusted \
    gnu-libiconv

# install and remove building packages
ENV PHPIZE_DEPS autoconf file g++ gcc libc-dev make pkgconf re2c php7-dev php7-pear \
    yaml-dev libevent-dev openssl-dev

# ENV PHP_INI_DIR /etc/php7

# RUN ln -s /usr/bin/php7 /usr/bin/php

RUN set -xe \
    && apk add --no-cache --repository "http://dl-cdn.alpinelinux.org/alpine/edge/testing" \
    --virtual .phpize-deps \
    $PHPIZE_DEPS \
    && sed -i 's/^exec $PHP -C -n/exec $PHP -C/g' $(which pecl) \
    && pecl channel-update pecl.php.net \
    && pecl install yaml \
    && echo "extension=yaml.so" > $PHP_INI_DIR/conf.d/01_yaml.ini
# RUN pecl install event
# RUN echo "extension=event.so" > $PHP_INI_DIR/conf.d/01_event.ini
RUN rm -rf /usr/share/php7 \
    && rm -rf /tmp/* \
    && apk del .phpize-deps

# COPY 00_memlimit.ini $PHP_INI_DIR/conf.d/00_memlimit.ini

WORKDIR /srv

ARG BUILD_DATE
ARG VCS_REF

LABEL org.label-schema.vcs-ref=$VCS_REF \
    org.label-schema.build-date=$BUILD_DATE

# Fix for iconv: https://github.com/docker-library/php/issues/240
ENV LD_PRELOAD /usr/lib/preloadable_libiconv.so php
