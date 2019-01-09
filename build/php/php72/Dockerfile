FROM alpine:3.7

MAINTAINER pmls63 <1083239138@qq.com>

## swoole版本，如需安装swoole则取消注释
ENV PHP_EXT_SWOOLE=swoole-2.2.0
ENV PHP_REDIS=4.0.2

ADD https://php.codecasts.rocks/php-alpine.rsa.pub /etc/apk/keys/php-alpine.rsa.pub

RUN apk --update add ca-certificates \
    && echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.7/main/" > /etc/apk/repositories \
    && echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.7/community/" >> /etc/apk/repositories \
    && echo " https://php.codecasts.rocks/v3.7/php-7.2" >> /etc/apk/repositories \
    && echo "nameserver 8.8.8.8" >> /etc/resolv.conf && apk update && apk upgrade

# install modules : GD iconv
RUN apk update && apk add -U \
    openssl \
    curl \
    wget \
    zip \
    unzip \
    git

RUN apk add -U \
    tini \
    php7 \
    php7-cli \
    php7-dev \
    php7-pear \
    php7-common \
    php7-apcu \
    php7-bcmath \
    php7-ctype \
    php7-curl \
    php7-exif \
    php7-iconv \
    php7-intl \
    php7-json \
    php7-mbstring \
    php7-opcache \
    php7-openssl \
    php7-pcntl \
    php7-pdo \
    php7-mysqlnd \
    php7-pdo_mysql \
    php7-pdo_pgsql \
    php7-phar \
    php7-posix \
    php7-session \
    php7-xml \
    php7-xsl \
    php7-zip \
    php7-zlib \
    php7-dom \
    php7-redis \
    php7-fpm \
    php7-gd \
    php7-mcrypt \
    php7-gmp \
    php7-mysqli \
    php7-pgsql \
    php7-gettext \
    php7-bz2 \
    php7-xml \
    php7-xmlrpc \
    php7-simplexml \
    curl curl-dev postgresql-dev \
    hiredis-dev libmcrypt-dev gmp-dev icu-dev linux-headers musl --virtual .phpize-deps $PHPIZE_DEPS \
    tzdata && \
    ln -fs /usr/bin/php7 /usr/bin/php && \
    rm -rf /var/cache/apk/ && mkdir /var/cache/apk && rm -rf /tmp/*

ADD swoole /root/swoole-src/

ADD build_swoole_so.sh /root/

RUN sh /root/build_swoole_so.sh

ADD rootfs /

ENTRYPOINT ["/sbin/tini", "--"]

CMD ["/usr/sbin/php-fpm7", "-R", "--nodaemonize"]

EXPOSE 9000

WORKDIR /app
