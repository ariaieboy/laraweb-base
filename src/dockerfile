FROM php:7.4-apache
# add apache conf so you can run your laravel by copy your project to /var/www/html
COPY docker/vhost.conf /etc/apache2/sites-available/000-default.conf
#install npm and php ext that needed for laravel 
RUN apt-get update && apt-get install -y \
      cron \
      libicu-dev \
      libpq-dev \
      libmcrypt-dev \
      libzip-dev \
      git \
      zip \
      unzip \
      npm \
      && rm -r /var/lib/apt/lists/* \
      && docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd \
          && docker-php-ext-install \
            intl \
            pcntl \
            pdo_mysql \
            pdo_pgsql \
            pgsql \
            zip \
            opcache
# update npm installation
RUN npm install npm@latest -g
# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer
# enabling apache rewrite
RUN a2enmod rewrite
