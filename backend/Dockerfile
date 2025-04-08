# Usa la imagen oficial de PHP con Nginx
FROM php:8.2-fpm

# Instalar dependencias necesarias
RUN apt-get update && apt-get install -y libpng-dev libjpeg-dev libfreetype6-dev git unzip && \
    docker-php-ext-configure gd --with-freetype --with-jpeg && \
    docker-php-ext-install gd pdo pdo_mysql

# Instalar Composer (gestor de dependencias para PHP)
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Establecer el directorio de trabajo
WORKDIR /var/www

# Copiar archivos de la aplicación Laravel
COPY . .

# Instalar dependencias de Laravel
RUN composer install

# Exponer el puerto 9000
EXPOSE 9000

# Comando para ejecutar PHP-FPM
CMD ["php-fpm"]
