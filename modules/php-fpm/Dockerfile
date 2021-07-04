FROM php:7.3-fpm

RUN apt-get update

RUN apt-get install -y --no-install-recommends \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libzip-dev \
    libzstd-dev \
    libpng-dev \
    libgeoip-dev \
    libxml2-dev \
    libbz2-dev \
    libmcrypt-dev \
    libldap2-dev \
    libpspell-dev \
    libmagickwand-dev \
    librrd-dev

RUN docker-php-ext-configure gd
RUN docker-php-ext-install gd
RUN docker-php-ext-install opcache
RUN docker-php-ext-install zip
RUN docker-php-ext-install soap
RUN docker-php-ext-install sockets
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install bz2
RUN docker-php-ext-install gettext
RUN docker-php-ext-install ldap
RUN docker-php-ext-install pspell
RUN docker-php-ext-install shmop
RUN docker-php-ext-install exif
RUN docker-php-ext-install pdo pdo_mysql

RUN pecl install geoip-1.1.1 \
    && docker-php-ext-enable geoip \
    && pecl install imagick \
    && docker-php-ext-enable imagick \
    && pecl install rrd \
    && docker-php-ext-enable rrd \
    && pecl install mcrypt \
    && docker-php-ext-enable mcrypt \
    && pecl install xdebug-2.9.1 \
    && docker-php-ext-enable xdebug \
    && pecl install igbinary \
    && docker-php-ext-enable igbinary \
    && yes | pecl install redis \
    && docker-php-ext-enable redis

RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin \
    && echo "alias composer='composer'" >> /root/.bashrc
