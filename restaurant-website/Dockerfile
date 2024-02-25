FROM php:8.3-fpm

WORKDIR /var/www/html

RUN apt-get update \
    && apt-get install -y libpng-dev libzip-dev libicu-dev unzip git \
    && docker-php-ext-install intl zip
# retirer sudo & autres paquets pas nécessaires

COPY --from=composer:latest /usr/bin/composer /usr/local/bin/composer

COPY . .

RUN chown -R www-data:www-data .

USER www-data

RUN composer install --no-dev --optimize-autoloader

RUN php bin/console asset-map:compile --env=prod

RUN php bin/console cache:clear --env=prod

USER root
