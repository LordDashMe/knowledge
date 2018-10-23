FROM jenkins/jenkins:lts

USER root

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
LABEL version="1.0.0"
LABEL description="Optimized Dockerfile for jenkins-php7.1."

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
    libapache2-mod-php7.1 \
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

COPY composer-install.sh /tmp/
RUN mv /tmp/composer-install.sh /var/www/composer-install.sh && \
    sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/7.1/fpm/php-fpm.conf && \
    echo "\ncgi.fix_pathinfo=0" >> /etc/php/7.1/fpm/php.ini && \
    echo "\nupload_max_filesize = 100M" >> /etc/php/7.1/fpm/php.ini && \
    echo "\npost_max_size = 100M" >> /etc/php/7.1/fpm/php.ini && \
    chown -R www-data:www-data /var/www && \ 
    find /var/www -type d -exec chmod 755 {} \; && \
    find /var/www -type f -exec chmod 644 {} \; && \
    chmod +x /var/www/composer-install.sh && \
    sh /var/www/composer-install.sh && \
    rm /var/www/composer-install.sh && \
    service php7.1-fpm start

USER jenkins

ENTRYPOINT ["/bin/bash"]
