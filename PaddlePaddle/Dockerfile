FROM python:3.7.4-slim

ARG DEBIAN_FRONTEND=noninteractive
WORKDIR /usr/share/workdir/

RUN pip install --upgrade pip \
    && apt-get install git -y \
    && python3 -m pip install paddlepaddle \
    && git clone https://github.com/PaddlePaddle/PaddleOCR.git \
    && pip install -r ./PaddleOCR/requirments.txt \
    && export PYTHONPATH=.

ENTRYPOINT [ "python" ]
