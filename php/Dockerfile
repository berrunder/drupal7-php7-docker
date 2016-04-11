FROM php:7.0-fpm

# install the PHP extensions we need
RUN apt-get update && apt-get install libpng12-dev libjpeg-dev libpq-dev git curl libmemcached-dev libfreetype6-dev libicu-dev g++ libxml2-dev -y \
	&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr --with-freetype-dir=/usr/ --enable-gd-native-ttf \
	&& docker-php-ext-install gd mbstring pdo_mysql zip \
	&& git clone https://github.com/php-memcached-dev/php-memcached /usr/src/php/ext/memcached \
	&& cd /usr/src/php/ext/memcached && git checkout -b php7 origin/php7 \
	&& docker-php-ext-configure memcached \
	&& docker-php-ext-install memcached intl soap \
	&& curl -sS https://getcomposer.org/installer | php \
	&& mv composer.phar /usr/local/bin/composer \
    && ln -s /usr/local/bin/composer /usr/bin/composer \
    && git clone https://github.com/drush-ops/drush.git /usr/local/src/drush \
    && cd /usr/local/src/drush \
    && git checkout 6.6.0 \
    && ln -s /usr/local/src/drush/drush /usr/bin/drush \
    && composer install \
    && apt-get clean \	
    && rm -rf /var/lib/apt/lists/*
