FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
        software-properties-common \
        python-software-properties \
        default-jre \
        default-jdk && \
    add-apt-repository ppa:webupd8team/java && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \ 
        oracle-java8-installer \
        wget \
        curl \
        zip \
        vim \
        git \
        cron \
        apt-utils
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
