
FROM ubuntu:16.04

run apt-get update && apt-get -y install \
    apt-utils \
    python-pip \
    cython \
    zlib1g-dev \    
    libbz2-dev \
    liblzma-dev \
    wget \
    bash \
    python3

WORKDIR /NGStools 



RUN  wget http://cab.spbu.ru/files/release3.13.1/SPAdes-3.13.1-Linux.tar.gz -O /tmp/spades.tar.gz && \
     tar -xvzf /tmp/spades.tar.gz -C /opt/ && \
     rm /tmp/spades.tar.gz

ENV PATH="/opt/SPAdes-3.13.1-Linux/bin/:${PATH}"





RUN pip install --upgrade pip

RUN pip install TETyper
