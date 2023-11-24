# ml-metadata package depends on tensorflow package
# 使用官方的 Ubuntu 20.04 镜像作为基础镜像
FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive
# 安装依赖包
RUN apt-get update
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get update -y
RUN apt-get install python3-distutils -y
RUN apt-get install -y python3.8 python3-pip

# 设置默认的 Python 版本
RUN update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 1

RUN python3 -m pip install distutils

COPY backend/metadata_writer/requirements.txt /kfp/metadata_writer/
RUN python3 -m pip install -r /kfp/metadata_writer/requirements.txt

COPY backend/metadata_writer/src/* /kfp/metadata_writer/
CMD python3 -u /kfp/metadata_writer/metadata_writer.py
