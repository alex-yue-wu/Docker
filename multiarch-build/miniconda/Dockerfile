FROM amazonlinux:2

ENV PATH /opt/conda/bin:$PATH

RUN yum -y --security update && \
    yum -y install \
    wget \
    tar \
    gzip \
    curl \
    git \
    ca-certificates \
    which \
    locate \
    yum clean all && \
    rm -rf /var/cache/yum

RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-py39_4.12.0-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    /opt/conda/bin/conda clean -tipsy && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    source ~/.bashrc

RUN conda config --add channels bioconda && \
    conda config --add channels conda-forge && \
    conda config --add channels defaults