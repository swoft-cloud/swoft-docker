ARG PHP_VERSION=7.1
FROM php:${PHP_VERSION}

LABEL maintainer="swoft-cloud swoft-docker <group@swoft.org>"

ARG PHPREDIS_VERSION=4.0.0
ARG HIREDIS_VERSION=0.13.3
ARG SWOOLE_VERSION=4.0.1
ARG PORT=9501

# Timezone
RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && echo 'Asia/Shanghai' > /etc/timezone

## Change Debian Source
ADD ./repositories/debian/sources  /etc/apt/sources.list

# Libs
RUN apt-get update \
    && apt-get install -y --allow-downgrades \
        curl \
        wget \
        git \
        zip \
        libssl-dev \
        libnghttp2-dev \
        libz-dev \
        libpcre3-dev \
        zlib1g=1:1.2.8.dfsg-2+b1 \
        zlib1g-dev=1:1.2.8.dfsg-2+b1 \
        libpcre3=2:8.35-3.3+deb8u4 \
        libpcre3-dev=2:8.35-3.3+deb8u4 \
    && apt-get clean \
    && apt-get autoremove

# Composer
RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer self-update --clean-backups

# PDO/Bcmath extension
RUN docker-php-ext-install pdo_mysql bcmath

# Redis extension
RUN wget http://pecl.php.net/get/redis-${PHPREDIS_VERSION}.tgz -O /tmp/redis.tar.tgz \
    && pecl install /tmp/redis.tar.tgz \
    && rm -rf /tmp/redis.tar.tgz \
    && docker-php-ext-enable redis

# Hiredis
RUN wget https://github.com/redis/hiredis/archive/v${HIREDIS_VERSION}.tar.gz -O hiredis.tar.gz \
    && mkdir -p hiredis \
    && tar -xf hiredis.tar.gz -C hiredis --strip-components=1 \
    && rm hiredis.tar.gz \
    && ( \
        cd hiredis \
        && make -j$(nproc) \
        && make install \
        && ldconfig \
    ) \
    && rm -r hiredis

# Swoole extension
RUN wget https://github.com/swoole/swoole-src/archive/v${SWOOLE_VERSION}.tar.gz -O swoole.tar.gz \
    && mkdir -p swoole \
    && tar -xf swoole.tar.gz -C swoole --strip-components=1 \
    && rm swoole.tar.gz \
    && ( \
        cd swoole \
        && phpize \
        && ./configure --enable-async-redis --enable-mysqlnd --enable-openssl --enable-http2 \
        && make -j$(nproc) \
        && make install \
    ) \
    && rm -r swoole \
    && docker-php-ext-enable swoole

ADD ./ /var/www/swoft

WORKDIR /var/www/swoft

EXPOSE ${PORT}

CMD ["php", "/var/www/swoft/bin/swoft", "start"]
