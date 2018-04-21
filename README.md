dnmp
=========================

[![Docker Hub](https://img.shields.io/badge/docker-ready-blue.svg)](https://registry.hub.docker.com/u/techdivision/dnmp-alpine/)
[![Docker Automated build](https://img.shields.io/docker/automated/techdivision/dnmp-alpine.svg)]()
[![php-fpm 7.2.4](https://img.shields.io/travis/php-v/symfony/symfony.svg)](http://php.net/)
[![MIT](https://img.shields.io/apm/l/vim-mode.svg)]()

通过docker-compose搭建的dnmp环境;

### Author
```
                     __     __________
    ____  ____ ___  / /____/ ___/__  /
   / __ \/ __ `__ \/ / ___/ __ \ /_ <
  / /_/ / / / / / / (__  ) /_/ /__/ /
 / .___/_/ /_/ /_/_/____/\____/____/
/_/
```

### Services
- nginx:alpine;
- php:alpine php-fpm 7.2.4;
- mysql:latest;
- redis:alpine;
- mongo:latest;

### Usage
1. Install `git`, `docker` and `docker-compose`;
2. Clone project:
  ```
  $ git clone https://github.com/pmls63/dnmp.git
  ```
3. Start docker:
  ```
  $ cd dnmp
  $ docker-compose up
  ```
4. Go to your browser and type `http://localhost`

### Table of Content
```
project                                                         根目录
├── Docker-compose.yml                                          docker-compose 文件
├── LICENSE                                                     license 文件
├── README.md                                                   readme 文件
├── build                                                       镜像构建目录 自定义镜像
│   ├── nginx
│   │   ├── Dockerfile                                          Dockerfile 用于构建自定义镜像
│   │   └── rootfs
│   │       └── etc
│   │           └── nginx
│   │               ├── conf.d
│   │               │   └── default.conf
│   │               └── nginx.conf
│   ├── php
│   │   └── php72
│   │       ├── Dockerfile
│   │       └── rootfs
│   │           └── etc
│   │               └── php7
│   │                   ├── conf.d
│   │                   │   ├── 00_opcache.ini
│   │                   │   └── 50-setting.ini
│   │                   └── php-fpm.conf
│   └── redis
│       ├── Dockerfile
│       └── docker-entrypoint.sh
├── conf                                                        配置文件目录
│   ├── mongodb
│   │   └── mongodb.conf                                        mongodb 配置文件
│   ├── mysql
│   │   ├── conf.d
│   │   └── my.cnf                                              mysql 配置文件
│   ├── nginx
│   │   ├── conf.d
│   │   │   ├── certs
│   │   │   │   └── ssl_test
│   │   │   │       ├── gencert.sh
│   │   │   │       ├── www.ssl_test.wls.crt
│   │   │   │       ├── www.ssl_test.wls.csr
│   │   │   │       ├── www.ssl_test.wls.key
│   │   │   │       └── www.ssl_test.wls.origin.key
│   │   │   ├── ssl_test.conf
│   │   │   └── test.conf
│   │   └── nginx.conf                                          nginx 配置文件
│   ├── php
│   │   ├── php-fpm.d
│   │   │   └── www.conf
│   │   └── php.ini                                             php 配置文件
│   └── redis
│       └── redis.conf                                          redis 配置文件
├── db                                                          数据库文件夹
│   ├── mongodb
│   ├── mysql
│   └── redis
├── log                                                         日志文件夹
│   ├── mongodb
│   ├── mysql
│   ├── nginx
│   ├── php-fpm
│   └── redis
└── www                                                         web项目文件夹
    ├── ssl_test
    │   └── index.php
    └── test
        └── index.php
```