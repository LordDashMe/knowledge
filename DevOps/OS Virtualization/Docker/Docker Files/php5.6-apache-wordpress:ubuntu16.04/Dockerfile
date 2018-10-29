FROM php5.6-apache:16.04

LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"

RUN apt-get update -y && apt-get install -y --no-install-recommends \
    subversion \
    mysql-client

ENTRYPOINT ["/bin/bash"]
