FROM php:5.6-fpm-alpine3.8

RUN apk add --no-cache --virtual .build-deps \
        $PHPIZE_DEPS \
    && pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug \
    && apk del .build-deps

RUN apk add --no-cache tzdata \
    && cp /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime \
    && echo "America/Sao_Paulo" > /etc/timezone

RUN echo "date.timezone=America/Sao_Paulo" \
    > /usr/local/etc/php/conf.d/timezone.ini

COPY xdebug.ini /usr/local/etc/php/conf.d/99-xdebug.ini

WORKDIR /var/www/html
