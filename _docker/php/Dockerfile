FROM php:7.3-fpm

WORKDIR /var/www

RUN apt-get update && apt-get install -y \
    bash \
    curl \
    zip \
    unzip \
    tzdata \
    libzip-dev \
    libssl-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libsodium-dev \
    libxml2-dev \
    libcurl4-openssl-dev \
    libonig-dev \
    && apt-get clean

RUN docker-php-ext-install \
    pdo_mysql \
    bcmath \
    gd \
    intl \
    opcache \
    mbstring \
    sodium \
    zip

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - \
    && apt-get install -y nodejs

# Устанавливаем Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN groupadd -g 1000 www \
    && useradd -u 1000 -g www -s /bin/bash -m www

USER www

CMD ["php-fpm"]