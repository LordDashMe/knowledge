FROM ubuntu:16.04
LABEL maintainer="Dash Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \ 
        software-properties-common \
        python-software-properties \
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
        lynx-cur \ 
        git-core \ 
        bash-completion && \
    echo "source /usr/share/bash-completion/completions/git" >> ~/.bashrc && \
    curl -sL https://deb.nodesource.com/setup_8.x | bash - && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \ 
        nodejs \
        build-essential
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
