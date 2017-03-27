FROM nginx:alpine

ADD nginx.conf /etc/nginx/
ADD web1.conf /etc/nginx/conf.d/web1.conf
ARG PHP7_UPSTREAM=php7
RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data \
    && rm /etc/nginx/conf.d/default.conf \
    && echo "upstream php7-upstream { server ${PHP7_UPSTREAM}:9000; } " >> /etc/nginx/conf.d/upstream.conf

CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80 8080
