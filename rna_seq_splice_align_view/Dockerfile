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
    libz-dev \
    unzip \
    gcc \
    wget \
    libssl-dev \
    build-essential \
    autoconf \
    automake \
    libtool \
    gettext \
    pkg-config \
    git \
    python-dev \
    libgsl-dev \
    libboost-all-dev \
    libsuitesparse-dev \
    liblpsolve55-dev \
    libsqlite3-dev \
    libmysql++-dev \
    libboost-iostreams-dev \
    zlib1g-dev \
    libbamtools-dev \
    zlib1g-dev \
    libhts-dev \
    libboost-all-dev 

RUN conda update -n base conda
RUN conda config --add channels bioconda
RUN conda config --add channels defaults
RUN conda config --add channels conda-forge
RUN conda install --yes \
    'jupyter' \
    'numpy' \
    'scipy' \
    'matplotlib' \
    'biopython' \
    'minimap2' \
    'star' \
    'trim-galore' \
    'igv'

RUN wget https://github.com/samtools/samtools/releases/download/1.15.1/samtools-1.15.1.tar.bz2 && \
    tar xjf samtools-1.15.1.tar.bz2 && \
    cd samtools-1.15.1 && \
    apt-get install --yes libncurses5-dev libbz2-dev && \
    ./configure --prefix=/software/samtools && \
    make && \
    make install

WORKDIR /work

CMD jupyter notebook --port=8888 --no-browser --ip='0.0.0.0' --allow-root

