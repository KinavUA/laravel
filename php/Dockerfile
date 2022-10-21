FROM composer:latest AS composer
FROM ubuntu:focal

COPY --from=composer /usr/bin/composer /usr/bin/composer


RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    git \
    php \
    php-xml \
    php-mysql \
    php-mbstring \
    php-zip \
    unzip \
    && apt-get clean


RUN cd /var/www/html/ \
    && git clone https://github.com/laravel/quickstart-basic \
    && cd quickstart-basic \
    && composer install \
    && sed -i -e "s/DB_HOST=.*/DB_HOST=db/" .env
