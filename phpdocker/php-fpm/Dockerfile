FROM phpdockerio/php:8.1-fpm
WORKDIR "/application"

# Install required PHP extensions
RUN apt-get update \
    && apt-get -y --no-install-recommends install \
        php8.1-bcmath \
        php8.1-calendar \
        php8.1-ctype \
        php8.1-curl \
        php8.1-date \
        php8.1-exif \
        php8.1-fileinfo \
        php8.1-gd \
        php8.1-iconv \
        php8.1-intl \
        php8.1-json \
        php8.1-mbstring \
        php8.1-mysqli \
        php8.1-openssl \
        php8.1-pdo \
        php8.1-pdo_mysql \
        php8.1-phar \
        php8.1-readline \
        php8.1-reflection \
        php8.1-session \
        php8.1-simplexml \
        php8.1-spl \
        php8.1-standard \
        php8.1-tokenizer \
        php8.1-xdebug \
        php8.1-xsl \
        php8.1-xml \
        php8.1-xmlreader \
        php8.1-xmlwriter \
        php8.1-zip \
        php8.1-zlib \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Copy application files
COPY . /application

# Install PHP dependencies and set permissions
RUN composer install --no-dev --optimize-autoloader \
    && chmod -R 777 storage bootstrap/cache

# Ensure PHP-FPM runs as the main process
CMD ["php-fpm"]
