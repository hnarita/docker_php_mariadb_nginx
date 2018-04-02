FROM php:7.1.1-fpm

COPY ./data/site /var/www/html
COPY ./web/php.ini /usr/local/etc/php/
RUN chmod 777 /var/www/html/fuel/app/logs

RUN docker-php-ext-install pdo pdo_mysql

RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev libmcrypt-dev zlib1g-dev git unzip \
  && docker-php-ext-install pdo_mysql mysqli mbstring gd iconv mcrypt zip

RUN apt-get install libldap2-dev -y && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-configure ldap --with-libdir=lib/x86_64-linux-gnu/ && \
    docker-php-ext-install ldap

RUN curl -sS https://getcomposer.org/installer | php

RUN mv composer.phar /usr/local/bin/composer
RUN composer self-update
RUN composer install --dev --no-interaction
