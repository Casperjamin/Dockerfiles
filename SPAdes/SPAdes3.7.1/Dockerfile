FROM ubuntu:16.04

RUN apt-get update && apt-get -y install \
    wget \
    python

WORKDIR /NGStools

RUN wget http://cab.spbu.ru/files/release3.7.1/SPAdes-3.7.1-Linux.tar.gz

RUN tar -xzf SPAdes-3.7.1-Linux.tar.gz

ENV PATH="/SPAdes-3.7.1-Linux/bin:$PATH"
