FROM ubuntu:16.04
LABEL maintainer="Dash Reyes <reyesjoshuaclifford@gmail.com>"
COPY 000-default.conf composer-install.bash /tmp/
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
        wget \
        curl \
        git \
        git-core \ 
        bash-completion && \
    echo "source /usr/share/bash-completion/completions/git" >> ~/.bashrc && \
    LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
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
        php5.6-gd \
        php5.6-mongo \
        php5.6-intl && \
    mv /tmp/000-default.conf /etc/apache2/sites-enabled/000-default.conf && \
    chmod +x /tmp/composer-install.bash && \
    sh /tmp/composer-install.bash && \
    rm /tmp/composer-install.bash && \
    a2enmod php5.6 && \
    a2enconf php5.6-fpm && \
    a2enmod rewrite && \
    a2enmod headers && \
    a2enmod proxy_fcgi setenvif && \
    cp /usr/lib/php/5.6/php.ini-development /etc/php/5.6/apache2 && \
    mv /etc/php/5.6/apache2/php.ini /etc/php/5.6/apache2/php.ini.bak && \
    mv /etc/php/5.6/apache2/php.ini-development /etc/php/5.6/apache2/php.ini && \
    sed -i "s/short_open_tag = On/short_open_tag = Off/" /etc/php/5.6/apache2/php.ini && \
    sed -i "s/date.timezone = ;/date.timezone = Asia\/Manila/" /etc/php/5.6/apache2/php.ini && \
    sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/5.6/apache2/php.ini && \
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
