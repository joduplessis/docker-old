FROM php:7.0-apache
MAINTAINER Jo du Plessis <jo@joduplessis.com>

# Install GD
RUN apt-get update \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd

# Install MCrypt
RUN apt-get update \
    && apt-get install -y libmcrypt-dev \
    && docker-php-ext-install mcrypt

# Install Intl
RUN apt-get update \
    && apt-get install -y libicu-dev \
    && docker-php-ext-install intl

# Install mbstring
RUN docker-php-ext-install mbstring

# Install soap
RUN apt-get update \
    && apt-get install -y libxml2-dev \
    && docker-php-ext-install soap

# Install PHP zip extension
RUN docker-php-ext-install zip

# Install xsl
RUN apt-get update \
    && apt-get install -y libxslt-dev \
    && docker-php-ext-install xsl

# Install PDO
RUN apt-get update && apt-get install -y libpng12-dev libjpeg-dev libpq-dev \
&& rm -rf /var/lib/apt/lists/* \
&& docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
&& docker-php-ext-install gd mbstring pdo pdo_mysql pdo_pgsql

# Define PHP_TIMEZONE env variable
ENV PHP_TIMEZONE Africa/Johannesburg

# Copy our virtual host file over
COPY ./000-default.conf /etc/apache2/sites-available/000-default.conf

# Enable Apache mod_rewrite
RUN a2enmod rewrite
RUN a2ensite 000-default.conf
RUN service apache2 restart
