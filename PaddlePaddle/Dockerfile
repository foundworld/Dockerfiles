FROM python:3.7.4-slim

RUN python3 -m pip install paddlepaddle

ARG DEBIAN_FRONTEND=noninteractive
RUN mkdir -p /usr/share/workdir/
WORKDIR /usr/share/workdir/

RUN apt-get install git -y \
    && git clone https://gitee.com/paddlepaddle/PaddleOCR \
    && cd PaddleOCR \
    && pip3 install -r requirments.txt

ENTRYPOINT [ "python" ]
