FROM ubuntu:latest

MAINTAINER Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>
RUN echo "This Dockerfile will work for Laravel structure."

RUN apt-get update -y

RUN apt-get install -y software-properties-common
RUN apt-get install -y python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

RUN apt-get update --fix-missing -y

# Install Nginx, PHP 5.6, and Other Supplimentary Programs (cron, git, vim, etc.)
RUN apt-get install -y nginx php5.6 php5.6-fpm php5.6-mbstring php5.6-curl php5.6-mcrypt php5.6-tokenizer php5.6-dom php5.6-zip php5.6-mysql php5.6-imap php5.6-xml php5.6-cli php5.6-gd
RUN apt-get install -y zip vim nano wkhtmltopdf libxrender1 git cron openssl lynx-cur php-xdebug php-gd

RUN echo "\ndaemon off;" >> /etc/nginx/site-nginx.conf
RUN sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/5.6/fpm/php-fpm.conf

RUN echo "\ncgi.fix_pathinfo=0" >> /etc/php/5.6/fpm/php.ini
RUN echo "\nupload_max_filesize = 100M" >> /etc/php/5.6/fpm/php.ini
RUN echo "\npost_max_size = 100M" >> /etc/php/5.6/fpm/php.ini

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
CMD cp /usr/lib/php/5.6/php.ini-development /etc/php/5.6/nginx
CMD mv /etc/php/5.6/nginx/php.ini /etc/php/5.6/nginx/php.ini.bak
CMD mv /etc/php/5.6/nginx/php.ini-development /etc/php/5.6/nginx/php.ini
