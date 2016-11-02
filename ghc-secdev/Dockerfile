FROM ubuntu:16.04
#docker build -t ghc-secdev ghc-secdev/
#docker run --rm -it ghc-secdev /bin/bash

RUN apt-get update
RUN apt-get install -y emacs24 curl wget vim git ssl-cert unzip build-essential libgmp-dev language-pack-en ispell iamerican-insane libtinfo-dev
RUN update-locale LANG=en_US.UTF-8
ENV LC_ALL=en_US.UTF-8
ENV TERM xterm-256color

RUN wget -qO- https://get.haskellstack.org/ | sh
ENV PATH /root/.local/bin:$PATH
COPY stack.yaml /root/.stack/global-project/stack.yaml
RUN stack setup
