FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
SHELL ["/bin/bash", "-c"]
COPY apache-config.conf /tmp/
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends software-properties-common python-software-properties \
        wget \
        curl \
        zip \
        vim \
        wkhtmltopdf \
        libxrender1 \
        git \
        composer \
        cron \
        openssl \
        apt-utils \
        lynx-cur \
        # https://stackoverflow.com/questions/36674667/png-h-file-not-found-linux
        libpng-dev \
        # https://community.c9.io/t/phpbrew-and-apache/3565/5
        apache2 \
        apache2-dev \
        # https://github.com/phpbrew/phpbrew/wiki/Requirement
        php7.0 \
        php7.0-curl \
        php7.0-json \
        php7.0-cgi \
        php7.0-fpm \
        autoconf \
        automake \
        libxml2-dev \
        libcurl4-openssl-dev \
        libssl-dev \
        openssl \
        gettext \
        libicu-dev \
        libmcrypt-dev \
        libmcrypt4 \
        libbz2-dev \
        libreadline-dev \
        build-essential \
        libmhash-dev \
        libmhash2 \
        libxslt1-dev \
        libjpeg-dev \
        libfreetype6-dev && \
    # https://github.com/phpbrew/phpbrew/wiki/Quick-Start
    # http://sandeep-bisht.blogspot.com/2017/08/phpbrew-install-php-53-in-ubuntu-1604.html
    curl -L -O https://github.com/phpbrew/phpbrew/raw/master/phpbrew && \
    chmod +x phpbrew && \
    mv phpbrew /usr/local/bin/phpbrew && \
    phpbrew init && \
    echo "[[ -e ~/.phpbrew/bashrc ]] && . ~/.phpbrew/bashrc" >> ~/.bashrc && \
    . ~/.phpbrew/bashrc && \
    phpbrew update --old && \
    phpbrew known && \
    phpbrew variants && \
    phpbrew --debug install 5.3.28 +bz2 +calendar +cli +gd +ctype +dom +iconv +fileinfo +filter +ipc +json +mbregex +mbstring +mhash +mcrypt +pcntl +pcre +pdo +phar +posix +readline +sockets +tokenizer +xml +curl +zip +mysql +intl +debug +apxs2 && \
    phpbrew use 5.3.28 && \
    phpbrew ext install gd -- --with-libdir=lib/i386-linux-gnu --with-gd=shared --enable-gd-native-ttf --with-jpeg-dir=/usr --with-png-dir=/usr && \
    # https://askubuntu.com/questions/453377/how-to-enable-event-mpm-apache-2-4-on-ubuntu-14-04-with-thread-safe-php
    a2dismod mpm_event && \
    a2enmod mpm_prefork && \
    a2enmod rewrite && \
    a2enmod headers && \
    a2enmod proxy_fcgi setenvif actions && \
    mv /tmp/apache-config.conf /etc/apache2/sites-enabled/000-default.conf && \
    echo "AddType application/x-httpd-php .php" >> /etc/apache2/mods-enabled/php5.load && \
    sed -i "s/short_open_tag = On/short_open_tag = Off/" ~/.phpbrew/php/php-5.3.28/etc/php.ini && \
    sed -i "s/date.timezone = ;/date.timezone = Asia\/Manila/" ~/.phpbrew/php/php-5.3.28/etc/php.ini && \
    sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" ~/.phpbrew/php/php-5.3.28/etc/php.ini && \
    echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    chown -R www-data:www-data /var/www && \
    find /var/www -type d -exec chmod 755 {} \; && \
    find /var/www -type f -exec chmod 644 {} \;
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
