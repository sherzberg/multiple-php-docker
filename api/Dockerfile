FROM php:5.6-fpm

WORKDIR /var/www

# Install modules
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        libicu-dev \
    && docker-php-ext-install iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-install mbstring zip intl

RUN echo "date.timezone=America/Chicago" > /usr/local/etc/php/conf.d/docker-php-ext-datetime.ini

RUN curl -sS https://getcomposer.org/installer | php
RUN ln -s /var/www/composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

ADD composer.json /var/www/
RUN composer install

ADD . /var/www/

CMD ["php-fpm"]
