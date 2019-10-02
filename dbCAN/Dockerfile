FROM ubuntu:18.04
MAINTAINER Ian Rambo ian.rambo@utexas.edu

USER root

RUN apt-get update && apt-get install -y apt-utils \
    default-jdk \
    zlib1g-dev \
    default-jre \
    software-properties-common \
    git \
    sudo \
    wget \
    diamond \
    hmmer \
    python2.7 \
    python-pip \
    && apt-get clean

RUN mkdir /build
RUN mkdir /build/DIAMOND && cd /build/DIAMOND \
    && wget http://github.com/bbuchfink/diamond/releases/download/v0.9.26/diamond-linux64.tar.gz \
    && tar -zxf diamond-linux64.tar.gz \
    && rm diamond-linux64.tar.gz
ENV PATH "$PATH:/build/DIAMOND"

RUN mkdir /build/dbCAN
RUN cd /build/dbCAN && wget http://bcb.unl.edu/dbCAN2/download/Tools/run_dbcan_v3.tar.gz \
    && tar -zxf run_dbcan_v3.tar.gz \
    && rm run_dbcan_v3.tar.gz \
    && cd run_dbcan/db \
    && hmmpress  dbCAN-HMMdb-V8.txt \
    && hmmpress stp.hmm \
    && hmmpress tf-1.hmm \
    && hmmpress tf-2.hmm \
    && diamond makedb --in CAZyDB.07312019.fa -d CAZy \
    && diamond makedb --in tcdb.fa -d tcdb \
    && pip install natsort
