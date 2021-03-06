FROM php:7.0-apache

COPY init/000-default.conf /etc/apache2/sites-available/

RUN apt-get update && apt-get install -y --allow-unauthenticated \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libjpeg-dev \
        libpng-dev \
        iproute2 \
        curl \
        git \
        zip \
        unzip \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install -j$(nproc) mbstring \
    && docker-php-ext-install -j$(nproc) mcrypt \
    && docker-php-ext-install -j$(nproc) mysqli \
    && docker-php-ext-install -j$(nproc) zip

RUN echo "ServerName $(ip route get 8.8.8.8 | awk '{print $NF; exit}')" >> /etc/apache2/apache2.conf && \
    echo '127.0.0.1 website.com' >> /etc/hosts && \
    echo "date.timezone = 'Pacific/Auckland'" >> /usr/local/etc/php/php.ini

RUN a2enmod rewrite && a2enmod headers
RUN service apache2 restart

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
