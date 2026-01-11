FROM php:8.2-fpm-bullseye

# Dependências do sistema
RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip \
    && rm -rf /var/lib/apt/lists/*

# Extensões PHP
RUN docker-php-ext-install mysqli pdo pdo_mysql

WORKDIR /var/www/html

COPY . .

RUN chown -R www-data:www-data /var/www/html
