FROM php5.6-apache:stable

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
LABEL version="1.0.0"
LABEL description="Optimized Dockerfile for php5.6-apache-laravel."

ADD apache-config-laravel.conf /etc/apache2/sites-enabled/000-default.conf

ENTRYPOINT ["/bin/bash"]