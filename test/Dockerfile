FROM php:7.4-apache

RUN apt-get update && apt-get install -y \
    unzip \
    curl \
    wget

# Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

COPY vhosts.conf /etc/apache2/sites-available/

# Enable PHP 7
RUN a2enmod rewrite
RUN a2enmod php7


RUN a2dissite 000-default.conf
RUN a2ensite vhosts.conf
RUN usermod -u 1000 www-data

WORKDIR /var/www/test-project

EXPOSE 80
