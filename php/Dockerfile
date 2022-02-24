FROM phpdockerio/php:8.1-fpm

WORKDIR /var/www/prettypost

ARG ADMIN_EMAIL
ARG ADMIN_NAME

RUN apt-get update; \
    apt-get -y --no-install-recommends install \
        zlib1g-dev g++ git libicu-dev zip libzip-dev zip \
        php8.1-imagick \ 
        php8.1-intl \
        php8.1-memcached \ 
        php8.1-pgsql \ 
        php8.1-redis \
        php8.1-xdebug; \
    docker-php-ext-install intl opcache pdo; \
    apt-get clean; \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN curl -sS https://get.symfony.com/cli/installer | bash
RUN mv /root/.symfony/bin/symfony /usr/local/bin/symfony
RUN git config --global user.email "$ADMIN_EMAIL" \ 
    && git config --global user.name "$ADMIN_NAME"