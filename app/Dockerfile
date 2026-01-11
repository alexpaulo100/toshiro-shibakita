FROM php:8.2-fpm

# Instala extensões necessárias
RUN docker-php-ext-install mysqli

# Define diretório de trabalho
WORKDIR /var/www/html

# Copia a aplicação
COPY . .

# Ajusta permissões
RUN chown -R www-data:www-data /var/www/html

EXPOSE 9000
