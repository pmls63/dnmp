FROM alpine:3.7

MAINTAINER pmls63 <1083239138@qq.com>

ADD https://php.codecasts.rocks/php-alpine.rsa.pub /etc/apk/keys/php-alpine.rsa.pub

RUN apk --update add ca-certificates \
    && echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.7/main/" > /etc/apk/repositories \
    && echo "https://mirror.tuna.tsinghua.edu.cn/alpine/v3.7/community/" >> /etc/apk/repositories \
    && echo "nameserver 8.8.8.8" >> /etc/resolv.conf && apk update && apk upgrade

RUN apk update && apk add -U \
    gcc g++ python python-dev py-pip make \
    libmemcached \
    openssl \
    libxml2 \
    libxml2-dev \
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
    php7-mysqli \
    php7-mysqlnd \
    php7-pgsql \
    php7-pdo \
    php7-pdo_mysql \
    php7-pdo_pgsql \
    php7-phar \
    php7-posix \
    php7-session \
    php7-xml \
    php7-xmlrpc \
    php7-simplexml \
    php7-xmlwriter \
    php7-xmlreader \
    php7-xsl \
    php7-zip \
    php7-zlib \
    php7-dom \
    php7-tokenizer \
    php7-redis \
    php7-sqlite3 \
    php7-fpm \
    php7-gd \
    php7-mcrypt \
    php7-gmp \
    php7-gettext \
    php7-bz2 \
    php7-zlib \
    librdkafka \
    librdkafka-dev \
    && rm -rf /var/cache/apk/*

ADD rootfs /

RUN cd /etc/soft \
&& pecl install mongodb-1.5.3.tgz
RUN echo "extension=mongodb.so" > /etc/php7/conf.d/mongodb.ini

RUN cd /etc/soft \
&& pecl install rdkafka-3.0.5.tgz
RUN echo "extension=rdkafka.so" > /etc/php7/conf.d/rdkafka.ini

RUN apk add -U \
    curl curl-dev postgresql-dev \
    hiredis-dev libmcrypt-dev gmp-dev icu-dev linux-headers musl --virtual .phpize-deps $PHPIZE_DEPS \
    tzdata && \
    ln -fs /usr/bin/php7 /usr/bin/php && \
    rm -rf /var/cache/apk/ && mkdir /var/cache/apk && rm -rf /tmp/*

ENTRYPOINT ["/sbin/tini", "--"]

CMD ["/usr/sbin/php-fpm7", "-R", "--nodaemonize"]

EXPOSE 9000

WORKDIR /app
