FROM ubuntu:16.04

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"

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
    lynx-cur

EXPOSE 80

ENTRYPOINT ["/bin/bash"]
