FROM python:3.7.4-slim

ARG DEBIAN_FRONTEND=noninteractive
WORKDIR /usr/share/workdir/

RUN apt-get clean \
    && apt-get update -y \
    && apt-get install git -y \
    && pip install --upgrade pip \
    && apt-get install gcc -y \
    && python3 -m pip install paddlepaddle \
    && git clone -b develop https://github.com/PaddlePaddle/PaddleOCR.git \
    && pip install -r ./PaddleOCR/requirments.txt \
    && apt-get purge --auto-remove -y wget git \
    && apt-get clean \
    && export PYTHONPATH=.

ENTRYPOINT [ "python" ]
