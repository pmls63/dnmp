dnmp
=========================

[![Docker Hub](https://img.shields.io/badge/docker-ready-blue.svg)](https://registry.hub.docker.com/u/techdivision/dnmp-alpine/)
[![Docker Automated build](https://img.shields.io/docker/automated/techdivision/dnmp-alpine.svg)]()
[![php-fpm 7.2.4](https://img.shields.io/travis/php-v/symfony/symfony.svg)](http://php.net/)
[![MIT](https://img.shields.io/apm/l/vim-mode.svg)]()

通过docker-compose搭建的dnmp环境;

### Author
                     __     __________
    ____  ____ ___  / /____/ ___/__  /
   / __ \/ __ `__ \/ / ___/ __ \ /_ <
  / /_/ / / / / / / (__  ) /_/ /__/ /
 / .___/_/ /_/ /_/_/____/\____/____/
/_/


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

### Construct
dnmp/
├── Docker-compose.yml
├── LICENSE
├── README.md
├── build
│   └── php
│       └── php72
│           └── Dockerfile
├── conf
│   ├── mongodb
│   │   └── mongodb.conf
│   ├── mysql
│   │   └── my.cnf
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
│   │   └── nginx.conf
│   ├── php
│   │   ├── php-fpm.d
│   │   │   └── www.conf
│   │   └── php.ini
│   └── redis
│       └── redis.conf
├── db
│   ├── mongodb
│   ├── mysql
│   └── redis
├── log
│   ├── mongodb
│   ├── mysql
│   ├── nginx
│   ├── php-fpm
│   └── redis
└── www
    ├── ssl_test
    │   └── index.php
    └── test
        └── index.php

