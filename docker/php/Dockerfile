FROM php:8.3-fpm

RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    libzip-dev \
    libxml2-dev \
    libicu-dev \
    libonig-dev \
    libcurl4-openssl-dev \
    unzip \
    nano \
    cron \
    imagemagick \
    jpegoptim \ 
    optipng \ 
    pngquant \
    gifsicle \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install mysqli \
    && docker-php-ext-install intl \
    && docker-php-ext-install opcache \
    && docker-php-ext-install bcmath \
    && docker-php-ext-install ctype \
    && docker-php-ext-install fileinfo \
    && docker-php-ext-install iconv \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install xml \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN apt-get update && apt-get install -y git 

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

COPY custom.ini /usr/local/etc/php/conf.d/

WORKDIR /var/www/html

#RUN composer create-project "typo3/cms-base-distribution:^12.4" .

RUN chown -R www-data:www-data /var/www/html
