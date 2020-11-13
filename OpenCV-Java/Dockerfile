FROM openjdk:8u252-jdk-slim

ARG DEBIAN_FRONTEND=noninteractive
ENV LANG C.UTF-8

RUN apt-get install -y cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
RUN apt-get install -y python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
RUN apt-get install -y ant

RUN mkdir -p /opencv && cd /opencv \
  && git clone https://github.com/opencv/opencv.git \
  && cd opencv && git checkout 4.4.0 \
  && git pull && mkdir build && cd build \
  && cmake -DBUILD_SHARED_LIBS=OFF -DCMAKE_BUILD_TYPE=RELEASE -DCMAKE_INSTALL_PREFIX=/usr/local/opencv -DBUILD_TESTS=OFF .. \
  && make -j$(nproc) \
  && make install
  
RUN echo $JAVA_HOME && echo $PATH

CMD /bin/sh
