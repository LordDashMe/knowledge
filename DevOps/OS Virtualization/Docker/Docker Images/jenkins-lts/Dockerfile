FROM jenkins/jenkins:lts

USER root

MAINTAINER Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>

RUN apt-get update
RUN apt-get install -y wget apt-utils

# PHP Repository.
RUN apt-get update --fix-missing -y

RUN apt install -y apt-transport-https ca-certificates
RUN wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg
RUN sh -c 'echo "deb https://packages.sury.org/php/ stretch main" > /etc/apt/sources.list.d/php.list'
RUN apt update

# Install PHP and Extensions.
RUN apt-get update
RUN apt-get install -y php7.1 php7.1-fpm php7.1-mbstring php7.1-curl php7.1-mcrypt php7.1-tokenizer php7.1-dom php7.1-zip php7.1-mysql php7.1-imap  php7.1-dev php7.1-xml php7.1-cli
RUN apt-get install -y zip vim nano wkhtmltopdf libxrender1 git cron openssl php-xdebug

# Configure PHP Setup.
RUN sed -i -e "s/;\?daemonize\s*=\s*yes/daemonize = no/g" /etc/php/7.1/fpm/php-fpm.conf
RUN echo "\ncgi.fix_pathinfo=0" >> /etc/php/7.1/fpm/php.ini
RUN echo "\nupload_max_filesize = 100M" >> /etc/php/7.1/fpm/php.ini
RUN echo "\npost_max_size = 100M" >> /etc/php/7.1/fpm/php.ini

# Install Composer.
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Start PHP.
RUN service php7.1-fpm start

USER jenkins