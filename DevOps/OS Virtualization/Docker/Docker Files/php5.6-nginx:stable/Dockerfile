FROM ubuntu:latest

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
LABEL version="1.0.0"
LABEL description="Optimized Dockerfile for php5.6-nginx."

RUN apt-get update -y && \
    apt-get install -y --no-install-recommends software-properties-common && \
    apt-get install -y --no-install-recommends python-software-properties && \
    LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
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
    apt-utils \
    lynx-cur \
    php-xdebug \
    php-gd \
    libapache2-mod-php5.6 \
    apache2 \
    php5.6 \
    php5.6-fpm \
    php5.6-mbstring \
    php5.6-curl \
    php5.6-mcrypt \
    php5.6-tokenizer \
    php5.6-dom \
    php5.6-zip \
    php5.6-mysql \
    php5.6-imap \
    php5.6-xml \
    php5.6-cli \
    php5.6-gd

COPY site-nginx.conf composer-install.sh /tmp/
RUN mv /tmp/site-nginx.conf /etc/nginx/sites-available/ && \
    mv /tmp/composer-install.sh /var/www/composer-install.sh && \
    ln -s /etc/nginx/sites-available/site-nginx.conf /etc/nginx/sites-enabled/site && \
    chown -R www-data:www-data /var/www && \ 
    find /var/www -type d -exec chmod 755 {} \; && \
    find /var/www -type f -exec chmod 644 {} \; && \
    cp /usr/lib/php/5.6/php.ini-development /etc/php/5.6/nginx && \
    mv /etc/php/5.6/nginx/php.ini /etc/php/5.6/nginx/php.ini.bak && \
    mv /etc/php/5.6/nginx/php.ini-development /etc/php/5.6/nginx/php.ini && \
    echo "\ndaemon off;" >> /etc/nginx/site-nginx.conf && \
    sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/5.6/fpm/php-fpm.conf && \
    echo "\ncgi.fix_pathinfo=0" >> /etc/php/5.6/fpm/php.ini && \
    echo "\nupload_max_filesize = 100M" >> /etc/php/5.6/fpm/php.ini && \
    echo "\npost_max_size = 100M" >> /etc/php/5.6/fpm/php.ini && \
    chmod +x /var/www/composer-install.sh && \
    sh /var/www/composer-install.sh && \
    rm /var/www/composer-install.sh

EXPOSE 80

ENTRYPOINT ["/bin/bash"]