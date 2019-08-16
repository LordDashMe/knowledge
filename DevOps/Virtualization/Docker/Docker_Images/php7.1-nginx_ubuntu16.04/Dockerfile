FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
COPY site-nginx.conf composer-install.bash /tmp/
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
        nginx \
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
        php7.1-gd \
        php7.1-intl && \
    mv /tmp/site-nginx.conf /etc/nginx/sites-available/ && \
    chmod +x /tmp/composer-install.bash && \
    sh /tmp/composer-install.bash && \
    rm /tmp/composer-install.bash && \
    ln -s /etc/nginx/sites-available/site-nginx.conf /etc/nginx/sites-enabled/site && \
    chown -R www-data:www-data /var/www && \ 
    find /var/www -type d -exec chmod 755 {} \; && \
    find /var/www -type f -exec chmod 644 {} \; && \
    echo "\ndaemon off;" >> /etc/nginx/site-nginx.conf && \
    sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/7.1/fpm/php-fpm.conf && \
    echo "\ncgi.fix_pathinfo = 0" >> /etc/php/7.1/fpm/php.ini && \
    echo "\nfile_uploads = On" >> /etc/php/7.1/fpm/php.ini && \
    echo "\nallow_url_fopen = On" >> /etc/php/7.1/fpm/php.ini && \
    echo "\nmemory_limit = 512M" >> /etc/php/7.1/fpm/php.ini && \
    echo "\nmax_execution_time = 360" >> /etc/php/7.1/fpm/php.ini && \
    echo "\nupload_max_filesize = 100M" >> /etc/php/7.1/fpm/php.ini && \
    echo "\npost_max_size = 100M" >> /etc/php/7.1/fpm/php.ini && \
    echo "\ndate.timezone = Asia\/Manila" >> /etc/php/7.1/fpm/php.ini
EXPOSE 80
CMD ["/bin/bash"]
