FROM php:8.0-apache

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf
RUN a2enmod rewrite

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
    locales apt-utils sudo git libicu-dev g++ libxml2-dev libzip-dev libonig-dev libxslt-dev unzip libpq-dev nodejs npm wget nano \
    libpng-dev libwebp-dev libjpeg62-turbo-dev libfreetype6-dev \
    apt-transport-https lsb-release ca-certificates wkhtmltopdf  

RUN echo "en_US.UTF-8 UTF-8" > /etc/locale.gen && \
    echo "fr_FR.UTF-8 UTF-8" >> /etc/locale.gen && \
    locale-gen
    

RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
   mv composer.phar /usr/local/bin/composer

RUN curl -sS https://get.symfony.com/cli/installer | bash \
    &&  mv /root/.symfony/bin/symfony /usr/local/bin

RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp && \
    docker-php-ext-install gd && \
    docker-php-ext-install mysqli && \
    docker-php-ext-install pdo && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install intl && \
    docker-php-ext-install opcache && \
    docker-php-ext-install exif && \
    docker-php-ext-install zip && \
    docker-php-ext-install calendar && \ 
    docker-php-ext-install dom && \ 
    docker-php-ext-install mbstring && \ 
    docker-php-ext-install xsl
    
RUN pecl install apcu && docker-php-ext-enable apcu

RUN npm install --global yarn

RUN git config --global user.email "xavier.burke@openpixl.fr" \
    &&  git config --global user.name "Xavier BURKE"

RUN useradd xavier -g www-data -d /home/xavier -m
RUN echo '%xavier ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN chown -R xavier:www-data /var/www
USER xavier

WORKDIR /var/www/html
