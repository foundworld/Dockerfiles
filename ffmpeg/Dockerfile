FROM openjdk:8u252-jdk-slim

ARG DEBIAN_FRONTEND=noninteractive
RUN sed -i s@/archive.ubuntu.com/@/mirrors.aliyun.com/@g /etc/apt/sources.list
RUN apt-get clean
RUN apt-get update --fix-missing -y
RUN apt-get install ffmpeg --fix-missing -y
