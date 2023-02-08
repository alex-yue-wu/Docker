FROM amazonlinux:2

ENV PATH /opt/conda/bin:$PATH

RUN yum -y --security update && \
    yum -y install \
    wget \
    tar \
    gzip \
    bzip2 \
    ca-certificates \
    curl \
    git \
    which \
    locate \
    zip \
    gcc-gfortran \
    gcc-c++ \
    readline-devel \
    ncurses-compat-libs \
    bzip2-devel.x86_64 \
    procps \
    yum clean all && \
    rm -rf /var/cache/yum

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda2-4.5.11-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    source ~/.bashrc

RUN conda install -y -c bioconda samtools=1.3.1 && \
    conda install -y -c bioconda pysam=0.8.4 && \
    conda install -y -c bioconda lumpy-sv=0.2.14a