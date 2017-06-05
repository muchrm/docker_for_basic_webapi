FROM nginx:alpine

ADD nginx.conf /etc/nginx/
ADD web0.conf /etc/nginx/conf.d/web0.conf
ARG PHP5_UPSTREAM=php5
RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data \
    && rm /etc/nginx/conf.d/default.conf \
    && echo "upstream php5-upstream { server ${PHP5_UPSTREAM}:9000; } " > /etc/nginx/conf.d/upstream.conf

CMD ["nginx", "-g", "daemon off;"]

EXPOSE 80 8080
