FROM php:7-apache

RUN apt-get update 

RUN apt-get install -y --no-install-recommends \
  unzip \
  unixodbc-dev \
  unixodbc \
  libpq-dev \
  libzip4 \
  libzip-dev \
  && rm -rf /var/lib/apt/lists/* \
  && docker-php-ext-install zip 

RUN docker-php-ext-install mysqli \
  && docker-php-ext-install pdo_mysql \
  && rm -rf /var/lib/apt/lists/*

RUN pecl install sqlsrv pdo_sqlsrv
RUN echo "extension=sqlsrv.so" >> /usr/local/etc/php/php.ini
RUN echo "extension=pdo_sqlsrv.so" >> /usr/local/etc/php/php.ini

RUN a2enmod rewrite

ADD 000-default.conf /etc/apache2/sites-available/

VOLUME ["/var/www/html"]

EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
