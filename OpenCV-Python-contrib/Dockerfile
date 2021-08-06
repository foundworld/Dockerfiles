FROM python:3.9-slim

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update -y && apt-get install -y build-essential \
    cmake \
    wget \
    git \
    unzip \
    yasm \
    pkg-config \
    libjpeg-dev \
    libtiff-dev \
    libpng-dev \
    libavcodec-dev \
    libavformat-dev \
    libswscale-dev \
    libv4l-dev \
    libatlas-base-dev \
    gfortran \
    libtbb2 \
    libtbb-dev \
    libpq-dev
RUN apt-get install -y tar libgtk2.0-dev
RUN apt-get install -y libdc1394-22-dev
RUN  apt-get -y clean all \
    && rm -rf /var/lib/apt/lists/*

RUN pip install numpy
WORKDIR /

RUN mkdir -p /opencv_contrib && cd /opencv_contrib \
  && wget -O opencv_contrib-src.tar.gz "https://github.com/opencv/opencv_contrib/archive/4.5.3.tar.gz" \
  && tar -xzf opencv_contrib-src.tar.gz --strip-components=1 \
  && mkdir -p /opencv && cd /opencv \
  && wget -O opencv-src.tar.gz "https://github.com/opencv/opencv/archive/4.5.3.tar.gz" \
  && tar -xzf opencv-src.tar.gz --strip-components=1 \
  && mkdir build && cd build \
        && cmake -DOPENCV_EXTRA_MODULES_PATH=/opencv_contrib/modules \
          -DBUILD_TIFF=ON \
          -DBUILD_opencv_java=OFF \
          -DBUILD_SHARED_LIBS=OFF \
          -DWITH_CUDA=OFF \
          -DENABLE_AVX=ON \
          -DWITH_OPENGL=ON \
          -DWITH_OPENCL=ON \
          -DWITH_IPP=ON \
          -DWITH_TBB=ON \
          -DWITH_EIGEN=ON \
          -DWITH_V4L=ON \
          -DBUILD_TESTS=OFF \
          -DBUILD_PERF_TESTS=OFF \
          -DCMAKE_BUILD_TYPE=RELEASE \
          -DBUILD_opencv_python3=ON \
          -DCMAKE_INSTALL_PREFIX=$(python3.9 -c "import sys; print(sys.prefix)") \
          -DPYTHON_EXECUTABLE=$(which python3.9) \
          -DPYTHON_INCLUDE_DIR=$(python3.9 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
          -DPYTHON_PACKAGES_PATH=$(python3.9 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") .. \
        && make install \
        && rm /opencv/opencv-src.tar.gz \
        && rm /opencv_contrib/opencv_contrib-src.tar.gz \
        && rm -r /opencv \
        && rm -r /opencv_contrib
ENTRYPOINT [ "python" ]
