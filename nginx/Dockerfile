ARG NGINX_VERSION=latest
FROM nginx:${NGINX_VERSION}

LABEL maintainer="swoft-cloud swoft-docker <group@swoft.org>"

COPY nginx.conf /etc/nginx/

ARG CHANGE_SOURCE=false
RUN if [ ${CHANGE_SOURCE} = true ]; then \
    # Change application source from dl-cdn.alpinelinux.org to aliyun source
    sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories \
;fi

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data

ARG UPSTREAM_CONTAINER=swoft
ARG UPSTREAM_PORT=9501

# Set upstream conf and remove the default conf
RUN echo "upstream swoft-upstream { server ${UPSTREAM_CONTAINER}:${UPSTREAM_PORT}; }" > /etc/nginx/conf.d/upstream.conf \
    && rm /etc/nginx/conf.d/default.conf

CMD ["nginx"]

EXPOSE 80 443
