FROM php:7.1-apache

RUN apt-get update
RUN apt-get install -y git zip zlib1g-dev
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev
RUN apt-get install -y mysql-client

RUN docker-php-ext-install mbstring
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install pdo
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install opcache
RUN docker-php-ext-install zip
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/  &&  \
            docker-php-ext-install gd
RUN apt-get install -y libssl-dev openssl
# RUN docker-php-ext-install phar

RUN apt-get clean \
  && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN a2enmod rewrite
RUN a2enmod headers
RUN apache2ctl -k graceful
