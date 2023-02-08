FROM amazonlinux:2

# Note: procps is required for use with Nextflow Tower 
RUN yum -y --security update && \
    yum -y install \
    wget \
    tar \
    gzip \
    curl \
    git \
    which \
    locate \
    zip \
    gcc-gfortran \
    gcc-c++ \
    readline-devel \
    ncurses-compat-libs \
    procps && \
    yum clean all && \
    rm -rf /var/cache/yum

ENV PATH /opt/conda/bin:$PATH
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-py39_4.12.0-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    source ~/.bashrc

RUN conda config --add channels bioconda && \
    conda install -y fgbio=2.0.2 && \
    conda install -y bwa=0.7.17 && \
    conda install -y picard=2.27.4 && \
    conda install -y samtools && \
    conda install -y fastp

# Basespace CLI
RUN wget "https://launch.basespace.illumina.com/CLI/latest/amd64-linux/bs" -O /opt/bs && \
    chmod a+x /opt/bs

ENV PATH /opt:$PATH