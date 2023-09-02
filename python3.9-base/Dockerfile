FROM python:3.9
MAINTAINER wx5223@gmail.com
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && echo 'Asia/Shanghai' > /etc/timezone
RUN apt-get update
RUN apt-get install -y --no-install-recommends vim-tiny && sed -i '$a\set nocompatible' /etc/vim/vimrc.tiny && sed -i '$a\set backspace=2' /etc/vim/vimrc.tiny
RUN apt-get install -y --no-install-recommends procps
RUN pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
ENV C_FORCE_ROOT=true
WORKDIR /work
