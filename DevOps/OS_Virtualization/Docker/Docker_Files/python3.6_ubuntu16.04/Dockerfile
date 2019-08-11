FROM ubuntu:16.04
LABEL maintainer="Dash Reyes <reyesjoshuaclifford@gmail.com>"
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
        git \
        git-core \ 
        bash-completion && \
    echo "source /usr/share/bash-completion/completions/git" >> ~/.bashrc && \
    add-apt-repository ppa:jonathonf/python-3.6 && \
    apt-get update -y && \
    apt-get install -y python3.6 && \
    update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 1 && \
    update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 2 && \
    update-alternatives --config python3 && \
    # https://askubuntu.com/a/1154616
    cp /usr/lib/python3/dist-packages/apt_pkg.cpython-35m-x86_64-linux-gnu.so /usr/lib/python3/dist-packages/apt_pkg.so && \
    # https://askubuntu.com/a/1121758
    add-apt-repository ppa:pypy/ppa && \
    apt-get update -y && \
    apt-get install -y pypy3 && \
    # https://www.rosehosting.com/blog/how-to-install-pip-on-ubuntu-16-04/
    apt-get install -y python3-pip && \
    pip3 install --upgrade pip && \
    # https://github.com/pypa/pip/issues/5447#issuecomment-407693701
    # https://github.com/pypa/pip/issues/5221#issuecomment-381568428
    hash -r pip3
EXPOSE 80
ENTRYPOINT ["/bin/bash"]
