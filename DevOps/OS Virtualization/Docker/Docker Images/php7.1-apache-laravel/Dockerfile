FROM ubuntu:latest

MAINTAINER Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>
RUN echo "This Dockerfile will work for Laravel structure."

RUN apt-get update -y

RUN apt-get install -y software-properties-common
RUN apt-get install -y python-software-properties
RUN LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php

RUN apt-get update --fix-missing -y

# Install Apache2, PHP 7.1, and Other Supplimentary Programs (cron, git, vim, etc.)
RUN apt-get install -y apache2 php7.1 php7.1-fpm php7.1-mbstring php7.1-curl php7.1-mcrypt php7.1-tokenizer php7.1-dom php7.1-zip php7.1-mysql php7.1-imap php7.1-xml php7.1-cli php7.1-gd
RUN apt-get install -y zip vim nano wkhtmltopdf libxrender1 git cron openssl lynx-cur php-xdebug php-gd libapache2-mod-php7.1

# Enable apache mods
RUN a2enmod php7.1
RUN a2enmod rewrite
RUN a2enmod headers

# Update the php.ini file, enable <? ?> tags and quieten logging.
RUN sed -i "s/short_open_tag = Off/short_open_tag= On/" /etc/php/7.1/apache2/php.ini
RUN sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/7.1/apache2/php.ini

# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid

RUN echo "ServerName localhost" >> /etc/apache2/apache2.conf

# Expose ports.
EXPOSE 80

# Update the default apache site with the following we created.
ADD apache-config-laravel.conf /etc/apache2/sites-enabled/000-default.conf

# Change permission in this folder.
RUN chown -R www-data:www-data /var/www \ 
    && find /var/www -type d -exec chmod 755 {} \; \
    && find /var/www -type f -exec chmod 644 {} \;

# Replace the php environment to development mode.
CMD cp /usr/lib/php/7.1/php.ini-development /etc/php/7.1/apache2
CMD mv /etc/php/7.1/apache2/php.ini /etc/php/7.1/apache2/php.ini.bak
CMD mv /etc/php/7.1/apache2/php.ini-development /etc/php/7.1/apache2/php.ini

# By default start up apache in the foreground, override with /bin/bash for interactive.
CMD /usr/sbin/apachectl -D FOREGROUND

# Define default command.
ENTRYPOINT service apache2 start && /bin/bash
