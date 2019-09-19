FROM php:7.3-cli

RUN apt-get update && \
    apt-get install -y \
    libmcrypt-dev \
    libzip-dev \
    git \
    unzip

RUN docker-php-ext-install -j$(nproc) \
    bcmath \
    pcntl \
    sockets \
    zip 

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /tmp
ENV COMPOSER_VERSION 1.9.0

RUN curl -s https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer

WORKDIR /app

ENTRYPOINT ["/usr/local/bin/composer"]