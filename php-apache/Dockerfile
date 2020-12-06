FROM php:7.4-apache

RUN apt-get update && apt-get install vim -y \
    && apt-get install nmap -y

#RUN echo "ServerName ubitransport.local" >> /ect/apache2/apache2.conf

RUN apt-get update \
    && apt-get install -y --no-install-recommends locales apt-utils git libicu-dev g++ libpng-dev libxml2-dev libzip-dev libonig-dev libxslt-dev;

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen \
    && echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen \
    && locale-gen

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && composer --version

RUN docker-php-ext-configure intl
RUN docker-php-ext-install pdo pdo_mysql gd opcache intl zip calendar dom mbstring zip gd xsl
RUN pecl install apcu && docker-php-ext-enable apcu

RUN cd /var/www \
    && git clone https://github.com/i-unlu/ubitransport-project.git \
    && cd /var/www/ubitransport-project \
    && composer install \
    && /var/www/ubitransport-project/vendor/bin/phpunit --migrate-configuration \
    && chmod -R 777 /var/www/ubitransport-project/var

COPY ./.env /var/www/ubitransport-project
COPY ./.env.test /var/www/ubitransport-project

#RUN cd /var/www/ubitransport-project \
#    && bin/console doc:mi:mi --dry-run \
#    && bin/console doc:mi:mi --env=test --dry-run

WORKDIR /var/www/ubitransport-project/
