FROM continuumio/miniconda3



RUN apt-get update &&\
    apt-get install -y \
    nano \
    htop \
    tree \
    curl \
    git \
    make \
    build-essential \
    libz-dev

RUN conda update -n base conda
RUN conda config --add channels bioconda
RUN conda config --add channels defaults
RUN conda config --add channels conda-forge
RUN conda install --yes \
    'braker2'
RUN conda install --yes \
    'jupyter' \
    'trim-galore' \
    'perl'\
    'perl-app-cpanminus'\
    'perl-hash-merge'\
    'perl-parallel-forkmanager'\
    'perl-scalar-util-numeric'\
    'perl-yaml'\
    'perl-class-data-inheritable'\
    'perl-exception-class'\
    'perl-test-pod'\
    'biopython'\
    'perl-file-which'\
    'perl-threaded'\
    'perl-list-util'\
    'perl-math-utils'\
    'cdbtools ' 


COPY gm_key_64.gz .
RUN gunzip ../gm_key_64.gz && mv ../gm_key_64 /root/.gm_key

WORKDIR /software
RUN wget ###Genemark Link### && \
    tar -xvzf gmes_linux_64_4.tar.gz && \
    cd /software/gmes_linux_64_4 && \
    perl change_path_in_perl_scripts.pl "/opt/conda/bin/perl"


ENV GENEMARK_PATH="/software/gmes_linux_64_4/"


RUN apt-get update &&\
    apt-get install -y \
    wget \
    autoconf \
    libgsl-dev \
    libboost-all-dev \
    libsuitesparse-dev \
    liblpsolve55-dev \
    libsqlite3-dev \
    libmysql++-dev \
    libboost-iostreams-dev \
    zlib1g-dev \
    libbamtools-dev zlib1g-dev \
    samtools \
    libhts-dev \
    libboost-all-dev \ 
    cdbfasta \
    diamond-aligner \
    libfile-which-perl \
    libparallel-forkmanager-perl \
    libyaml-perl \
    libdbd-mysql-perl \
    python3-biopython 

RUN git clone https://github.com/Gaius-Augustus/Augustus.git && \
    cd Augustus && \
    make augustus && \
    make auxprogs

ENV AUGUSTUS_SCRIPTS_PATH="/software/Augustus/scripts"
ENV AUGUSTUS_CONFIG_PATH="/software/Augustus/config/"
ENV AUGUSTUS_BIN_PATH="/software/Augustus/bin/"

RUN conda install --yes \
    'sra-tools' \
    'hisat2' \
    'repeatmasker' \
    'repeatmodeler'

RUN wget https://github.com/samtools/samtools/releases/download/1.15.1/samtools-1.15.1.tar.bz2 && \
    tar xjf samtools-1.15.1.tar.bz2 && \
    cd samtools-1.15.1 && \
    apt-get install --yes libncurses5-dev libbz2-dev && \
    ./configure --prefix=/software/samtools && \
    make && \
    make install

WORKDIR /work

CMD jupyter notebook --port=8888 --no-browser --ip='0.0.0.0' --allow-root