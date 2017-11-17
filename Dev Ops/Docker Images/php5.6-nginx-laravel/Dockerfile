FROM ubuntu:latest

MAINTAINER Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>

RUN apt-get update -y

RUN apt-get install -y software-properties-common
RUN apt-get install -y python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

RUN apt-get update -y

# Install nginx, php5.6, etc.
RUN apt-get install -y nginx php5.6 php5.6-fpm php5.6-mbstring php5.6-curl php5.6-mcrypt zip vim nano php5.6-mysql wkhtmltopdf libxrender1 cron git openssl

RUN echo "\ndaemon off;" >> /etc/nginx/site-nginx.conf
RUN sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/5.6/fpm/php-fpm.conf

RUN echo "\ncgi.fix_pathinfo=0" >> /etc/php/5.6/fpm/php.ini
RUN echo "\nupload_max_filesize = 100M" >> /etc/php/5.6/fpm/php.ini
RUN echo "\npost_max_size = 100M" >> /etc/php/5.6/fpm/php.ini

# Nginx config.
RUN rm /etc/nginx/sites-enabled/default
ADD ./site-nginx.conf /etc/nginx/sites-available/
RUN ln -s /etc/nginx/sites-available/site-nginx.conf /etc/nginx/sites-enabled/site

# Change permission in this folder.
RUN chown -R www-data:www-data /var/www \ 
    && find /var/www -type d -exec chmod 755 {} \; \
    && find /var/www -type f -exec chmod 644 {} \;

# Expose ports.
EXPOSE 80

# Replace the php environment to development mode.
CMD cp /usr/lib/php/5.6/php.ini-development /etc/php/5.6/apache2
CMD mv /etc/php/5.6/apache2/php.ini /etc/php/5.6/apache2/php.ini.bak
CMD mv /etc/php/5.6/apache2/php.ini-development /etc/php/5.6/apache2/php.ini

# Define default command.
ENTRYPOINT service nginx start && service php5.6-fpm start && /bin/bash
