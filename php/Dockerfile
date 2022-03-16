FROM php:7.3-fpm

LABEL maintainer="Konstantin Prishvin <kostya.php@gmail.com>"

# Arguments defined in docker-compose.yml
ARG USER
ARG UID

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    curl \
    wget \
    zip \
    unzip \
    # for php-intl
    libicu-dev \
    # for php-snmp
    libsnmp-dev \
    # for php-gd
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev \
    # for php-zip
    libzip-dev
    # libonig-dev \
    # libxml2-dev \

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

# Install PHP extensions
RUN docker-php-ext-install \
        intl \
        snmp \
        gd \
        zip \
        pdo \
        pdo_mysql \
        mbstring \
        exif \
        pcntl \
        bcmath \
    && pecl install xdebug \
    && docker-php-ext-enable \
        xdebug

# Get latest Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Create system user to run Composer
RUN useradd -G www-data,root -u $UID -d /home/$USER $USER \
    && mkdir -p /home/$USER/.composer \
    && chown -R $USER:$USER /home/$USER

# Custom config
ADD php.ini /usr/local/etc/php/conf.d/40-custom.ini

WORKDIR /var/www

USER $USER

EXPOSE 9000 9003

CMD ["php-fpm"]
