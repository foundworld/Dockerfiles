FROM ubuntu:20.10

RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN apt-get clean

RUN apt-get update -y \
    && apt-get install apt-utils -y \
    && apt-get upgrade -y \
    && apt-get dist-upgrade -y \
    && mkdir -p /workdir

ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get install wget -y \
    && mkdir -p /tmp/python3.7/ && cd /tmp/python3.7 && wget https://www.python.org/ftp/python/3.7.4/Python-3.7.4.tgz \
    && tar -xvzf Python-3.7.4.tgz \
    && cd Python-3.7.4 \
    && apt-get install libbz2-dev libncurses5-dev libgdbm-dev libgdbm-compat-dev liblzma-dev libsqlite3-dev libssl-dev openssl tk-dev uuid-dev libreadline-dev -y \
    && apt-get install libffi-dev -y \
    && ./configure --with-ssl --prefix=/usr/local/python3 --enable-optimizations \
    && make && make install \
    && ln -s /usr/local/python3/bin/python3.7 /usr/bin/python3 \
    && ln -s /usr/local/python3/bin/pip3.7 /usr/bin/pip3 \
    && pip3 install --upgrade pip

ENTRYPOINT [ "python3" ]
# You can base on this image to add more package/tools
