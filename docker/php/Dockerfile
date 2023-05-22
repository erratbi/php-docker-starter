FROM php:8.2-fpm

# Set Current Directory
WORKDIR /var/www/vhosts/

# Install dependencies
RUN apt-get clean && apt-get update && apt-get upgrade -y && apt-get install -y \
    git \
    libcurl4-openssl-dev \
    libonig-dev \
    libpng-dev \
    libssl-dev \
    libicu-dev \
    libxml2-dev \
    libzip-dev \
    unzip \
    wget \
    zip \
    tzdata

RUN docker-php-ext-configure intl
# PHP Extensions
RUN docker-php-ext-install \
    bcmath \
    exif \
    gd \
    mysqli \
    opcache \
    pdo_mysql \
    pcntl \
    xml \
    zip \
    intl

# Install Composer from Official Docker Image
# https://hub.docker.com/_/composer
COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer


# Install Redis extension
RUN pecl install redis && \
    docker-php-ext-enable redis


RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
RUN sed -i -e "s/upload_max_filesize = 2M/upload_max_filesize = 100M/g" "$PHP_INI_DIR/php.ini"
COPY config/php.ini "$PHP_INI_DIR/99-custom.ini"
