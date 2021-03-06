FROM ubuntu:bionic

ARG DEBIAN_FRONTEND=noninteractive
ENV LANG C.UTF-8

RUN apt-get clean
RUN apt-get update -y

RUN apt-get install -y openjdk-8-jdk \
  && export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64 \
  && export PATH=$PATH:$JAVA_HOME/bin

RUN apt-get install -y cmake git wget tar libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
RUN apt-get install -y python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev
RUN apt-get install -y ant

RUN mkdir -p /opencv && cd /opencv \
  && wget -O opencv-src.tar.gz "https://github.com/opencv/opencv/archive/4.4.0.tar.gz" \
  && tar -xzf opencv-src.tar.gz --strip-components=1 \
  && mkdir build && cd build \
  && cmake -DBUILD_SHARED_LIBS=OFF -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr/local/opencv -DBUILD_TESTS=OFF .. \
  && make -j$(nproc) \
  && make install
  
RUN echo $JAVA_HOME && echo $PATH

CMD /bin/sh
