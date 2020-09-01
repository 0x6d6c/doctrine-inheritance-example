FROM php:7.1-apache

RUN mkdir --parents /var/www/html/public
COPY 000-default.conf /etc/apache2/sites-available

# Use `apt-get' instead of simply `apt' that is not suitable for scripts.
RUN apt-get update --fix-missing

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN apt-get install -y \
    git \
    # Required for Composer to download dist packages
    zip unzip

RUN docker-php-ext-install \
    pdo_mysql

RUN printf '[PHP]\ndate.timezone = "Europe/Warsaw"\n' >> /usr/local/etc/php/conf.d/date.ini
