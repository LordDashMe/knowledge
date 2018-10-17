FROM php7.1-apache:stable

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
LABEL version="1.0.0"
LABEL description="Optimized Dockerfile for php7.1-apache-symfony."

ADD apache-config-symfony.conf /etc/apache2/sites-enabled/000-default.conf

ENTRYPOINT ["/bin/bash"]
