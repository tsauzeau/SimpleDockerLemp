FROM php:7.0-fpm

COPY php.ini /usr/local/etc/php/

RUN echo "php_flag[display_errors] = On">>/usr/local/etc/php-fpm.conf
RUN echo "php_admin_flag[log_errors] = On">>/usr/local/etc/php-fpm.conf
RUN echo "php_admin_value[display_errors] = 'stderr'">>/usr/local/etc/php-fpm.conf

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd

CMD ["php-fpm"]
