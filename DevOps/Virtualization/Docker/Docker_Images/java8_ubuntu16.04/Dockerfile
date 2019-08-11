FROM ubuntu:16.04
LABEL maintainer="Dash Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
        default-jre \
        default-jdk && \
    add-apt-repository ppa:webupd8team/java && \
    apt-get update -y && \
    apt-get install -y --no-install-recommends \ 
        oracle-java8-installer \
        git \
        git-core \ 
        bash-completion && \
    echo "source /usr/share/bash-completion/completions/git" >> ~/.bashrc
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
