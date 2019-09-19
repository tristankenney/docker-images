FROM php:7.3-cli

RUN apt-get update && \
    apt-get install -y \
    libmcrypt-dev \
    libzip-dev 

RUN docker-php-ext-install -j$(nproc) \
    bcmath \
    pcntl \
    zip 

COPY --from=composer /usr/bin/composer /usr/bin/composer
COPY  --from=composer /docker-entrypoint.sh /docker-entrypoint.sh

WORKDIR /app

ENTRYPOINT ["/bin/sh", "/docker-entrypoint.sh"]

CMD ["composer"]