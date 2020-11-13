FROM openjdk:8u212-jre-alpine3.9

ENV LANG C.UTF-8

ENV OPENCV_VERSION 4.4.0
ENV OPENCV_SRC_URL "https://github.com/opencv/opencv/archive/$OPENCV_VERSION.tar.gz"
ENV OPENCV_INSTALL_PREFIX "/usr/local/opencv"
ENV OPENCV_JAVA_PATH "$OPENCV_INSTALL_PREFIX/share/OpenCV/java"

RUN set -x \
  && apk add --no-cache libstdc++

RUN set -x \
    && apk add --no-cache --virtual .build-dependencies \
        cmake \
        tar \
        ca-certificates \
        make \
        g++ \
        linux-headers \
        python \
    
    && export PATH=$PATH:$JAVA_HOME/bin \
    && mkdir -p /tmp/ant && cd /tmp/ant \
    && wget -O apache-ant.tar.gz "http://archive.apache.org/dist/ant/binaries/apache-ant-1.10.1-bin.tar.gz" \
    && tar -xzf apache-ant.tar.gz --strip-components=1 \
    && export ANT_HOME=/tmp/ant \
    && export PATH=$PATH:$ANT_HOME/bin \
    && mkdir -p /tmp/opencv && cd /tmp/opencv \
    && wget -O opencv-src.tar.gz "$OPENCV_SRC_URL" \
    && tar -xzf opencv-src.tar.gz --strip-components=1 \
    && mkdir build && cd build \
    && cmake \
        -DCMAKE_BUILD_TYPE=RELEASE \
        -DCMAKE_INSTALL_PREFIX="$OPENCV_INSTALL_PREFIX" \
        -DBUILD_SHARED_LIBS=OFF \
        -DBUILD_EXAMPLES=OFF \
        -DBUILD_TESTS=OFF \
        -DBUILD_PERF_TESTS=OFF \
        -DBUILD_JAVA=ON \
        .. \
    && echo $JAVA_HOME \
    && echo $PATH \
    && make -j$(nproc) \
    && make install \
    && cd / \
    && apk del .build-dependencies \
    && rm -r /tmp/*

CMD /bin/sh
