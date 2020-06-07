FROM python:3.7.4-slim

ARG DEBIAN_FRONTEND=noninteractive
WORKDIR /usr/share/workdir/

RUN pip install --upgrade pip 
RUN apt-get install git -y 
RUN python3 -m pip install paddlepaddle 
RUN git clone -b develop https://github.com/PaddlePaddle/PaddleOCR.git
RUN ls -l
RUN pip install -r ./PaddleOCR/requirments.txt
RUN export PYTHONPATH=.

ENTRYPOINT [ "python" ]
