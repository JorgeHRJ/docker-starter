# Sites PHP Container

# Base from Amazon Linux
FROM amazonlinux:2017.09

MAINTAINER Jorge Hernández Ríos <jorgehrios94@gmail.com>

# PHP packages installation
RUN yum install -y git unzip vim php71-fpm php71-cli php71-pdo php71-zip php71-mysqlnd php71-memcached php71-pecl-imagick php71-gd php71-gmp php71-mbstring

# Create App User
RUN groupadd -g 33 -o app
RUN useradd -d /home/builds -u 33 -g 33 -s /sbin/nologin app

# Configure PHP CLI
COPY etc/php-7.1.d/customs.ini /etc/php-7.1.d/

# Configure PHP FPM
COPY etc/php-fpm-7.1.d/www.conf /etc/php-fpm-7.1.d/

# Create Caches
RUN mkdir -p /var/lib/php/7.1/session
RUN mkdir -p /var/lib/php/7.1/wsdlcache
RUN mkdir -p /var/lib/php/7.1/opcache
RUN chown 33:33 -R /var/lib/php

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

# Expose
EXPOSE 9000

# Run
WORKDIR /home/app

CMD ["php-fpm-7.1", "-F"]
