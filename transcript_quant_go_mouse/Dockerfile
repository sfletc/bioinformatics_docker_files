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
    perl \
    libssl-dev \
    build-essential \
    autoconf \
    automake \
    libtool \
    gettext \
    pkg-config \
    swig \
    ruby \
    git \
    python-dev \
    libcurl4-openssl-dev

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
    'r-base=4.2.2' \
    'r-biocmanager' \
    'salmon' \
    'trim-galore'

RUN conda install --yes \
    'bioconductor-goseq' \
    'bioconductor-deseq2' \
    'bioconductor-org.mm.eg.db' \
    'bioconductor-txdb.mmusculus.ucsc.mm39.refgene' \
    'bioconductor-txdb.mmusculus.ucsc.mm10.ensgene' 

RUN conda install --yes \
    'r-pheatmap'
RUN conda install --yes \
    'r-dplyr'
RUN conda install --yes \
    'r-sessioninfo'

RUN wget https://github.com/curl/curl/releases/download/curl-7_87_0/curl-7.87.0.tar.gz && \
    tar xvzf curl-7.87.0.tar.gz && \
    cd curl-7.87.0 && \
    ./configure --with-openssl && \
    make && \ 
    make install

RUN R -e 'BiocManager::install("tximport", update=TRUE, ask=FALSE)'

RUN R -e 'install.packages(c("repr", "IRdisplay", "IRkernel"), type = "source", dependencies=TRUE, repos="http://cran.rstudio.com/")'
RUN R -e 'IRkernel::installspec()'
RUN R -e 'install.packages(c("gprofiler2", "readr"), type = "source", dependencies=TRUE, repos="http://cran.rstudio.com/")'
WORKDIR /work

CMD jupyter notebook --port=8888 --no-browser --ip='0.0.0.0' --allow-root

