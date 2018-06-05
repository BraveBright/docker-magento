FROM php:7.1-apache

RUN apt-get update \
  && apt-get install -y \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng12-dev \
    libxslt1-dev \
    mysql-client \
    vim \
  && docker-php-ext-configure \
    gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
  && docker-php-ext-install \
    bcmath \
    calendar \
    dom \
    exif \
    gd \
    gettext \
    intl \
    mbstring \
    mcrypt \
    mysqli \
    pdo_mysql \
    sockets \
    wddx \
    xsl \
    opcache \
    zip \
    soap \
  && a2enmod rewrite \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
  && useradd -m bravebright9

COPY conf/ /etc/apache2/

RUN a2dissite 000-default \
  && a2ensite sandbox
