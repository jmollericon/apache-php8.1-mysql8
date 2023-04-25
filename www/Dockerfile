FROM php:7.0-apache
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN docker-php-ext-configure calendar && docker-php-ext-install calendar
RUN apt-get update && apt-get upgrade -y

# Install Postgre PDO
RUN apt-get install -y libpq-dev \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql

RUN docker-php-ext-install mysqli pdo pdo_mysql

RUN apt-get -y install libmcrypt-dev
RUN a2enmod rewrite

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN pecl config-set php_ini "${PHP_INI_DIR}/php.ini"
# RUN pecl install mcrypt-1.0.1 && docker-php-ext-enable mcrypt;
