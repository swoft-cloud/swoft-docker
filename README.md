<p align="center">
    <a href="https://github.com/swoft-cloud/swoft" target="_blank">
        <img src="http://qiniu.daydaygo.top/swoft-logo.png?imageView2/2/w/300" alt="swoft" />
    </a>
</p>

[![Latest Version](https://img.shields.io/badge/beta-v1.0.0-green.svg?maxAge=2592000)](https://github.com/swoft-cloud/swoft/releases)
[![Build Status](https://travis-ci.org/swoft-cloud/swoft.svg?branch=master)](https://travis-ci.org/swoft-cloud/swoft)
[![Php Version](https://img.shields.io/badge/php-%3E=7.0-brightgreen.svg?maxAge=2592000)](https://secure.php.net/)
[![Swoole Version](https://img.shields.io/badge/swoole-%3E=2.1.3-brightgreen.svg?maxAge=2592000)](https://github.com/swoole/swoole-src)
[![Hiredis Version](https://img.shields.io/badge/hiredis-%3E=0.1-brightgreen.svg?maxAge=2592000)](https://github.com/redis/hiredis)
[![Swoft Doc](https://img.shields.io/badge/docs-passing-green.svg?maxAge=2592000)](https://doc.swoft.org)
[![Swoft License](https://img.shields.io/hexpm/l/plug.svg?maxAge=2592000)](https://github.com/swoft-cloud/swoft/blob/master/LICENSE)

**[中文说明](README_CN.md)**

## Introduction

The first high-performance PHP coroutine full-stack componentization framework based on Swoole native coroutine, built-in coroutine web server and commonly-used coroutine client, resident memory, which has no dependency on PHP-FPM, asynchronous non-blocking IO implementation, similar to synchronous client style of writing to achieve the use of asynchronous clients, without complex asynchronous callback, no tedious yield, similar  Go language coroutines, flexible annotations framework, a powerful global dependency injection container base on annotations, and great service governance , flexible and powerful AOP, PSR specification implementation, etc., could be used to build high-performance Web systems, APIs, middleware, basic services, microservice and so on.

- Base on Swoole extension
- Built-in HTTP, TCP, WebSocket Server
- Poweful AOP (Aspect Oriented Programming)
- Flexible and comprehensive annotations framework
- Global dependency injection container
- PSR-7 based HTTP message implementation
- PSR-14 based event manager
- PSR-15 based middleware
- PSR-16 based cache design
- Scalable high performance RPC
- Great service governance, fallback, load balance, service registration and discovery
- Database ORM
- Universal connection pool
- Mysql, Redis, RPC, HTTP Coroutine Clients
- Coroutine driver client and blocking driver client seamlessly switch automatically
- Coroutine and asynchronous task delivery
- Custom user process
- RESTful support
- Internationalization (i18n) support
- High performance router
- Fast and flexible parameter validator
- Alias mechanism
- Powerful log component
- Cross-platform application auto-reload


## Document

[**Chinese Document**](https://doc.swoft.org)  
[**English Document**](https://doc.swoft.org) Not yet, please help us write it.

QQ Group: 548173319/778656850

## Introduction

Swoft-docker is a base on docker-compose service choreography repository that allows you to quickly build a complete swoft environment based on docker containerization.

**Note: locate the directory where the `swoft` project is located so that the `swoft-docker` project and the `swoft` project are in the same directory**

## Environmental Requirements

1. docker engine release 17.06.0+

2. [docker-compose release 1.14.0+](https://github.com/docker/compose/releases/tag/1.14.0)

**reference to: [Compose file version 3 reference](https://docs.docker.com/compose/compose-file/#reference-and-guidelines)**

## Usage

```
./sync.sh <options>
Available options:
   install		 Installs docker-sync gem on the host machine.
   up [services]	 Starts docker-sync and runs docker compose.
   down			 Stops containers and docker-sync.
   bash			 Opens bash on the workspace.
   sync			 Manually triggers the synchronization of files.
   clean		 Removes all files from docker-sync.
```

Copy `env-example` to `.env`, build the mirror and create the container by running `./sync.sh up`.

## docker for linux

Here, if your operating system is `Linux`, then **recommends** to modify several configuration items under `.env`.

- APP_CODE_PATH_CONTAINER_MODE=:cached

```
docker-compose -f docker-compose.yml up
```

## docker for mac

Here, we use `docker-sync` to solve the problem of disk synchronization under MAC system.

```
./sync.sh install
```

Here, if your operating system is `OSX`, then you **must** modify several configuration items under `.env`.

- APP_CODE_PATH_CONTAINER_MODE=:nocopy
- DOCKER_SYNC_STRATEGY=native_osx

```
./sync.sh up
```

## License

Swoft is an open-source software licensed under the [LICENSE](LICENSE)
