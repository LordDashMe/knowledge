FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends software-properties-common python-software-properties && \
    apt-get install -y --no-install-recommends \
    wget \
    curl \
    zip \
    vim \
    wkhtmltopdf \
    libxrender1 \
    git \
    cron \
    openssl \
    apt-utils \
    lynx-cur
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
