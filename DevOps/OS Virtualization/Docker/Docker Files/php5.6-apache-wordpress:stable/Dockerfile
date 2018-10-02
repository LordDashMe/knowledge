FROM php5.6-apache:stable

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
LABEL version="1.0.0"
LABEL description="Optimized Dockerfile for php5.6-apache-wordpress."

RUN apt-get update -y && apt-get install -y --no-install-recommends \
    subversion \
    mysql-client

ENTRYPOINT ["/bin/bash"]