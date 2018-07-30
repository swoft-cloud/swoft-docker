ARG REDIS_VERSION=latest
FROM redis:${REDIS_VERSION}

LABEL maintainer="swoft-cloud swoft-docker <group@swoft.org>"

RUN mkdir -p /usr/local/etc/redis
COPY ./conf/redis.conf /usr/local/etc/redis/redis.conf

VOLUME /data

EXPOSE 6379

CMD ["redis-server", "/usr/local/etc/redis/redis.conf"]