dnmp
=========================

[![Docker Hub](https://img.shields.io/badge/docker-ready-blue.svg)](https://registry.hub.docker.com/u/techdivision/dnmp-alpine/)
[![Docker Automated build](https://img.shields.io/docker/automated/techdivision/dnmp-alpine.svg)]()
[![php-fpm 7.2.4](https://img.shields.io/travis/php-v/symfony/symfony.svg)](http://php.net/)
[![MIT](https://img.shields.io/apm/l/vim-mode.svg)]

通过docker-compose搭建的dnmp环境;

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

