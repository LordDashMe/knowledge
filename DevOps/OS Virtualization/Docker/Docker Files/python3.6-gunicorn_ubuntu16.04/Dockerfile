FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends software-properties-common && \
    apt-get install -y --no-install-recommends python-software-properties && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \
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
        lynx-cur && \
    apt-get install -y \
        python3.6 \
        pypy && \
    pip install gunicorn
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
