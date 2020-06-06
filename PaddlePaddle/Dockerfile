FROM python:3.7.4-slim

RUN python3 -m pip install paddlepaddle

ARG DEBIAN_FRONTEND=noninteractive
RUN mkdir -p /usr/share/workdir/
WORKDIR /usr/share/workdir/

RUN pip install --upgrade pip \
    && apt-get install git -y \
    && git clone https://github.com/PaddlePaddle/PaddleOCR.git \
    && cd PaddleOCR \
    && pip3 install -r requirments.txt

ENTRYPOINT [ "python" ]
