FROM php:8.2-apache

# Instala extensões necessárias do PHP
RUN docker-php-ext-install mysqli

# Habilita o mod_rewrite do Apache (boa prática)
RUN a2enmod rewrite

# Copia o código da aplicação para o container
COPY . /var/www/html/

# Ajusta permissões
RUN chown -R www-data:www-data /var/www/html

EXPOSE 80
