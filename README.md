dnmp
=========================

[![php-fpm 7.2.4](https://img.shields.io/travis/php-v/symfony/symfony.svg)](http://php.net/)



通过docker-compose搭建的dnmp环境
nginx:alpine
php:alpine php-fpm 7.2.4
mysql:latest
redis:alpine
mongo:latest

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

