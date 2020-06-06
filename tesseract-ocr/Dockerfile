FROM ubuntu:20.10

ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get clean \
    && apt-get update -y \
    && apt-get install apt-utils -y \
    && apt-get upgrade -y \
    && apt-get dist-upgrade -y \
    && apt-get install wget -y \
    && mkdir -p /tmp/python3.8/ && cd /tmp/python3.8 \
    && wget https://www.python.org/ftp/python/3.8.3/Python-3.8.3.tgz \
    && tar -xvzf Python-3.8.3.tgz \
    && cd Python-3.8.3 \
    && apt-get install libbz2-dev libncurses5-dev libgdbm-dev libgdbm-compat-dev liblzma-dev libsqlite3-dev libssl-dev openssl tk-dev uuid-dev libreadline-dev -y \
    && apt-get install libffi-dev -y \
    && ./configure --with-ssl --prefix=/usr/local/python3 --enable-optimizations \
    && make && make install \
    && ln -s /usr/local/python3/bin/python3.8 /usr/bin/python3 \
    && ln -s /usr/local/python3/bin/pip3.8 /usr/bin/pip3 \
    && pip3 install --upgrade pip \
    && apt-get install tesseract-ocr -y \
    && apt-get install libtesseract-dev -y \
    && apt-get install clang -y \
    && apt-get install curl -y \
    && mkdir -p /usr/local/share/tessdata/ \
    && curl -o /usr/local/share/tessdata/eng.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/eng.traineddata \
    && curl -o /usr/local/share/tessdata/chi_sim.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/chi_sim.traineddata \
    && curl -o /usr/local/share/tessdata/chi_sim_vert.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/chi_sim_vert.traineddata \
    && curl -o /usr/local/share/tessdata/chi_tra.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/chi_tra.traineddata \
    && curl -o /usr/local/share/tessdata/chi_tra_vert.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/chi_tra_vert.traineddata \
    && curl -o /usr/local/share/tessdata/HanS.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/script/HanS.traineddata \
    && curl -o /usr/local/share/tessdata/HanS_vert.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/script/HanS_vert.traineddata \
    && curl -o /usr/local/share/tessdata/HanT.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/script/HanT.traineddata \
    && curl -o /usr/local/share/tessdata/HanT_vert.traineddata \
       https://raw.githubusercontent.com/tesseract-ocr/tessdata_best/master/script/HanT_vert.traineddata \
    && rm -rf /tmp/python3.8 \
    && apt-get purge --auto-remove -y \
    autoconf \
    automake \
    build-essential \
    ca-certificates \
    curl \
    git \
    libtool \
  && apt-get clean

ENTRYPOINT [ "python3" ]
