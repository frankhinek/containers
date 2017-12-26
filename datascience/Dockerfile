FROM ubuntu:16.04

LABEL maintainer="Frank Hinek <frank.hinek@gmail.com>"

ENV CONDA_DIR /opt/conda
ENV PATH $CONDA_DIR/bin:$PATH

# Install Miniconda
# Based on https://hub.docker.com/r/conda/miniconda3/~/dockerfile/
RUN apt-get -qq update && apt-get -qq -y install curl bzip2 \
    && mkdir -p $CONDA_DIR \
    && echo export PATH=$CONDA_DIR/bin:'$PATH' > /etc/profile.d/conda.sh \
    && curl -sSL https://repo.continuum.io/miniconda/Miniconda3-4.3.31-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && echo "5551f01f436b6409d467412c33e12ecc4f43b5e029290870f8fdeca403c274e6  /tmp/miniconda.sh" | sha256sum -c - \
    && bash /tmp/miniconda.sh -bfp $CONDA_DIR \
    && rm -rf /tmp/miniconda.sh \
    && conda install -y python=3.6 \
    && conda update conda \
    && apt-get -qq -y remove curl bzip2 \
    && apt-get -qq -y autoremove \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* /var/log/dpkg.log \
    && conda clean --all --yes

# Install Data Science Python Packages
RUN pip --no-cache-dir install \
        Pillow \
        h5py \
        matplotlib \
        numpy \
        pandas \
        scipy \
        sklearn
