FROM php:8.3-fpm

WORKDIR /var/www/html

RUN apt-get update \
    && apt-get install -y libpng-dev libzip-dev libicu-dev unzip sudo nginx git \
    && docker-php-ext-install intl zip \
# retirer sudo & autres paquets pas nécessaires

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

COPY composer.json composer.json
COPY public public
COPY src src
COPY assets assets
COPY templates templates
COPY bin bin
COPY config config
COPY tests tests

RUN chown -R www-data:www-data .

USER www-data

# Incohérence avec le sujet
RUN composer install --no-dev --optimize-autoloader

# Incohérence avec le sujet
RUN php bin/console asset-map:compile --env=prod

RUN php bin/console cache:clear --env=prod

USER root
