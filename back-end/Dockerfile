FROM php:8.2-apache

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"
COPY ./docker/php-custom.ini-development $PHP_INI_DIR/conf.d/php-custom.ini

RUN apt-get update && apt-get install -y \
zip \
unzip \
git \
libzip-dev \
libpng-dev \
libjpeg-dev \
libfreetype6-dev

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN docker-php-ext-configure gd --with-jpeg && \
    docker-php-ext-install mysqli pdo pdo_mysql zip gd

# For Code Coverage generation via PHPUnit
RUN yes | pecl install xdebug \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.mode=coverage" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

COPY . /var/www/html/
# RUN composer update \
#     && composer install

# CMD ["php", "artisan", "serve", "--host=0.0.0.0", "--port", "8000"]

CMD sh -c "composer install && php artisan serve --host=0.0.0.0 --port 8000"

EXPOSE 8000