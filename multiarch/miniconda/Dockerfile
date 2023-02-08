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
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-py39_22.11.1-1-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    # /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    source ~/.bashrc

# RUN conda config --add channels bioconda && \
#     conda install -y -c bioconda fgbio=2.0.2 && \
#     conda install -y -c bioconda bwa=0.7.17 && \
#     conda install -y -c bioconda picard=2.27.4 && \
#     conda install -y -c bioconda samtools && \
#     conda install -y -c bioconda fastp

# ENV CONDA_SUBDIR=osx-64
# RUN conda env config vars set CONDA_SUBDIR=osx-64

RUN conda config --add channels bioconda && \
    conda config --add channels conda-forge && \
    conda config --add channels defaults

RUN conda install -y fgbio=2.0.2

# RUN conda install -y fgbio=2.0.2 && \
#     conda install -y bwa=0.7.17 && \
#     conda install -y picard=2.27.4 && \
#     conda install -y samtools && \
#     conda install -y fastp

# # Basespace CLI
# RUN wget "https://launch.basespace.illumina.com/CLI/latest/amd64-linux/bs" -O /opt/bs && \
#     chmod a+x /opt/bs

# ENV PATH /opt:$PATH