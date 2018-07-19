FROM ubuntu:latest

MAINTAINER Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>

RUN echo "This Dockerfile will work for Laravel folder structure only!"

RUN apt-get update -y
RUN apt-get install -y software-properties-common
RUN apt-get install -y python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

# Supplimentary Programs (cron, git, vim, etc.)
RUN apt-get update --fix-missing -y && apt-get install -y \
    wget \
    curl \
    zip \
    vim \
    nano \
    wkhtmltopdf \
    libxrender1 \
    git \
    cron \
    openssl \
    lynx-cur \
    php-xdebug \
    php-gd \
    libapache2-mod-php7.1

# Install Apache2, PHP 7.1 and Extensions related.
RUN apt-get update --fix-missing -y && apt-get install -y \ 
    apache2 \
    php7.1 \
    php7.1-fpm \
    php7.1-mbstring \
    php7.1-curl \
    php7.1-mcrypt \
    php7.1-tokenizer \
    php7.1-dom \
    php7.1-zip \
    php7.1-mysql \
    php7.1-imap \
    php7.1-xml \
    php7.1-cli \
    php7.1-gd

# Install PHP Composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer
RUN php -r "unlink('composer-setup.php');"

RUN echo "\ndaemon off;" >> /etc/nginx/site-nginx.conf
RUN sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/7.1/fpm/php-fpm.conf

RUN echo "\ncgi.fix_pathinfo=0" >> /etc/php/7.1/fpm/php.ini
RUN echo "\nupload_max_filesize = 100M" >> /etc/php/7.1/fpm/php.ini
RUN echo "\npost_max_size = 100M" >> /etc/php/7.1/fpm/php.ini

# Nginx config.
RUN rm /etc/nginx/sites-enabled/default
ADD site-nginx-laravel.conf /etc/nginx/sites-available/
RUN ln -s /etc/nginx/sites-available/site-nginx.conf /etc/nginx/sites-enabled/site

# Change permission in this folder.
RUN chown -R www-data:www-data /var/www \ 
    && find /var/www -type d -exec chmod 755 {} \; \
    && find /var/www -type f -exec chmod 644 {} \;

# Expose ports.
EXPOSE 80

# Replace the php environment to development mode.
RUN cp /usr/lib/php/7.1/php.ini-development /etc/php/7.1/nginx
RUN mv /etc/php/7.1/nginx/php.ini /etc/php/7.1/nginx/php.ini.bak
RUN mv /etc/php/7.1/nginx/php.ini-development /etc/php/7.1/nginx/php.ini

ENTRYPOINT ["/bin/bash"]
