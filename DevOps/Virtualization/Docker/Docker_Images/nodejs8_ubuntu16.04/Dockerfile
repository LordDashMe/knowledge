FROM ubuntu:16.04
LABEL maintainer="Joshua Clifford Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \ 
        # https://askubuntu.com/a/1000120
        software-properties-common \
        wget \
        curl \
        git \
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
