FROM php:7.1-apache

RUN apt-get update \
  && apt-get install -y \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
    mysql-client \
  && docker-php-ext-configure \
    gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install \
    bcmath \
    calendar \
    exif \
    gd \
    gettext \
    intl \
    mcrypt \
    mysqli \
    pcntl \
    pdo_mysql \
    soap \
    sockets \
    wddx \
    xsl \
    opcache \
    zip \
  && a2enmod rewrite \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
  && useradd -m apache \
  && chsh -s /bin/bash apache

COPY envvars /etc/apache2/envvars

RUN a2dissite 000-default.conf \
  && rm /etc/apache2/sites-available/000-default.conf \
  && rm /etc/apache2/sites-available/default-ssl.conf

# USER apache

WORKDIR /var/www/magento
