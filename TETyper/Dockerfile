
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
    python3 \
    gcc \
    libz-dev \
    make \
    libncurses5-dev

WORKDIR /NGStools/



# install SPAdes
RUN  wget http://cab.spbu.ru/files/release3.13.1/SPAdes-3.13.1-Linux.tar.gz -O /tmp/spades.tar.gz && \
     tar -xvzf /tmp/spades.tar.gz -C /opt/ && \
     rm /tmp/spades.tar.gz

ENV PATH="/opt/SPAdes-3.13.1-Linux/bin/:${PATH}"



#install TETyper

RUN pip install --upgrade pip

RUN pip install TETyper



ENV samtools_version 1.9
ENV bcftools_version 1.9
ENV htslib_version 1.9

WORKDIR /usr/local/bin/

#download tools
RUN wget https://github.com/samtools/samtools/releases/download/${samtools_version}/samtools-${samtools_version}.tar.bz2
RUN wget https://github.com/samtools/bcftools/releases/download/${bcftools_version}/bcftools-${bcftools_version}.tar.bz2
RUN wget https://github.com/samtools/htslib/releases/download/${htslib_version}/htslib-${htslib_version}.tar.bz2

# extract files for the suite of tools
RUN tar -xjf /usr/local/bin/samtools-${samtools_version}.tar.bz2 -C /usr/local/bin/
RUN tar -xjf /usr/local/bin/bcftools-${bcftools_version}.tar.bz2 -C /usr/local/bin/
RUN tar -xjf /usr/local/bin/htslib-${htslib_version}.tar.bz2 -C /usr/local/bin/

# run make on the source
RUN cd /usr/local/bin/htslib-${htslib_version}/ && ./configure
RUN cd /usr/local/bin/htslib-${htslib_version}/ && make
RUN cd /usr/local/bin/htslib-${htslib_version}/ && make install

RUN cd /usr/local/bin/samtools-${samtools_version}/ && ./configure
RUN cd /usr/local/bin/samtools-${samtools_version}/ && make
RUN cd /usr/local/bin/samtools-${samtools_version}/ && make install

RUN cd /usr/local/bin/bcftools-${bcftools_version}/ && make
RUN cd /usr/local/bin/bcftools-${bcftools_version}/ && make install





