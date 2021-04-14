FROM php:5-apache

RUN apt-get update 

RUN apt-get install -y --no-install-recommends \
  unzip \
  unixodbc-dev \
  unixodbc \
  libpq-dev \
  libzip4 \
  libzip-dev \
  && docker-php-ext-install zip 

RUN docker-php-ext-install mysql \
  && docker-php-ext-install mysqli \
  && docker-php-ext-install pdo_mysql

RUN apt-get install -y apt-utils freetds-dev 

RUN docker-php-ext-configure mssql --with-libdir=lib/x86_64-linux-gnu && \
  docker-php-ext-install mssql

RUN docker-php-ext-configure pdo_dblib --with-libdir=lib/x86_64-linux-gnu && \
  docker-php-ext-install pdo_dblib

RUN echo "date.timezone = America/Sao_Paulo" >> /usr/local/etc/php/php.ini

RUN a2enmod rewrite

RUN rm -rf /var/lib/apt/lists/*

ADD 000-default.conf /etc/apache2/sites-available/

VOLUME ["/var/www/html"]

EXPOSE 80
EXPOSE 443

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
