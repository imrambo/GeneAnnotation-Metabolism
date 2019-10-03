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
    r-base \
    samtools \
    bamtools \
    prodigal \
    hmmer \
    wget \
    bwa


RUN cpan -i Data::Dumper \
    #&& cpan -i POSIX qw(strftime) \
    && cpan -i Excel::Writer::XLSX \
    && cpan -i Getopt::Long \
    && cpan -i Statistics::Descriptive \
    && cpan -i Array::Split qw(split_by split_into) \
    && cpan -i Bio::SeqIO \
    && cpan -i Bio::Perl \
    && cpan -i Bio::Tools::CodonTable \
    && cpan -i Carp

RUN mkdir /build
RUN cd /build && wget https://github.com/wwood/CoverM/archive/v0.2.0-alpha7.tar.gz \
    && tar -zxf v0.2.0-alpha7.tar.gz \
    && rm v0.2.0-alpha7.tar.gz

RUN cd /build && git clone https://github.com/AnantharamanLab/METABOLIC.git
