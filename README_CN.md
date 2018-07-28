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

**[English](README.md)**

## 简介

首个基于 Swoole 原生协程的新时代 PHP 高性能协程全栈组件化框架，内置协程网络服务器及常用的协程客户端，常驻内存，不依赖传统的 PHP-FPM，全异步非阻塞 IO 实现，以类似于同步客户端的写法实现异步客户端的使用，没有复杂的异步回调，没有繁琐的 yield，有类似 Go 语言的协程、灵活的注解、强大的全局依赖注入容器、完善的服务治理、灵活强大的 AOP、标准的 PSR 规范实现等等，可以用于构建高性能的Web系统、API、中间件、基础服务等等。

- 基于 Swoole 扩展
- 内置协程 HTTP, TCP, WebSocket 网络服务器
- 强大的 AOP (面向切面编程)
- 灵活完善的注解功能
- 全局的依赖注入容器
- 基于 PSR-7 的 HTTP 消息实现
- 基于 PSR-14 的事件管理器
- 基于 PSR-15 的中间件
- 基于 PSR-16 的缓存设计
- 可扩展的高性能 RPC
- 完善的服务治理，熔断，降级，负载，注册与发现
- 数据库 ORM
- 通用连接池
- 协程 Mysql, Redis, RPC, HTTP 客户端
- 协程和同步阻塞客户端无缝自动切换
- 协程、异步任务投递
- 自定义用户进程
- RESTful 支持
- 国际化(i18n)支持
- 高性能路由
- 快速灵活的参数验证器
- 别名机制
- 强大的日志系统
- 跨平台热更新自动 Reload


## 文档

[**中文文档**](https://doc.swoft.org)

1. QQ Swoft 官方1群: 548173319

2. QQ Swoft 官方2群: 778656850

## 仓库简介

swoft-docker是一个基于docker-compose的服务编排仓库，让你可以快速基于docker容器化搭建配套的swoft环境。

<font color="red">注意：找到 `swoft` 项目的所在的目录，让 `swoft-docker` 项目和 `swoft` 项目处于同一级目录下</font>

## 使用

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

把 `env-example` 复制为 `.env`，通过运行 `./sync.sh up` 来构建镜像和创建容器。

## 关于Mac for docker磁盘同步问题

这里，我们借助了 `docker-sync` 来解决mac系统下磁盘同步的问题。

```
./sync.sh install
```

在这里，如果你的操作系统是 `OSX` 的话，那么，你必须修改 `.env` 下的几个配置项

- APP_CODE_PATH_CONTAINER_MODE=:nocopy
- DOCKER_SYNC_STRATEGY=native_osx

## 协议

Swoft 的开源协议为 Apache-2.0，详情参见[LICENSE](LICENSE)
