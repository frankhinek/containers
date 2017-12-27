ARG cuda_version=9.0
ARG cudnn_version=7
FROM nvidia/cuda:${cuda_version}-cudnn${cudnn_version}-runtime-ubuntu16.04

LABEL maintainer="Frank Hinek <frank.hinek@gmail.com>"

ENV CONDA_DIR /opt/conda
ENV PATH $CONDA_DIR/bin:$PATH

# Install Miniconda
# Based on https://hub.docker.com/r/conda/miniconda3/~/dockerfile/
RUN apt-get -qq update && apt-get -qq -y install bzip2 curl unzip wget \
    && mkdir -p $CONDA_DIR \
    && echo export PATH=$CONDA_DIR/bin:'$PATH' > /etc/profile.d/conda.sh \
    && curl -sSL https://repo.continuum.io/miniconda/Miniconda3-4.3.31-Linux-x86_64.sh -o /tmp/miniconda.sh \
    && echo "5551f01f436b6409d467412c33e12ecc4f43b5e029290870f8fdeca403c274e6  /tmp/miniconda.sh" | sha256sum -c - \
    && bash /tmp/miniconda.sh -bfp $CONDA_DIR \
    && rm -rf /tmp/miniconda.sh \
    && conda update conda \
    && apt-get -qq -y remove bzip2 \
    && apt-get -qq -y autoremove \
    && apt-get autoclean \
    && rm -rf /var/lib/apt/lists/* /var/log/dpkg.log \
    && conda clean --all --yes

# Using Python 3.5 until there is a protobuf 3.1 pip package for 3.6
# Reference: https://www.tensorflow.org/install/install_linux
ARG python_version=3.5

# Install Python and Data Science Packages
RUN conda install -y python=${python_version} \
    && pip --no-cache-dir install \
        Pillow \
        h5py \
        matplotlib \
        numpy \
        pandas \
        scipy \
        scikit-learn \
    && conda clean --all --yes

# Install TensorFlow Dependencies
# Based on https://github.com/tensorflow/tensorflow/blob/master/tensorflow/tools/docker/Dockerfile
RUN apt-get -qq update && apt-get -qq  -y install --no-install-recommends \
        build-essential \
        libfreetype6-dev \
        libpng12-dev \
        libzmq3-dev \
        pkg-config \
        rsync \
        software-properties-common \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Custom binary C++ based protobuf pip package
ENV protobuf_url=https://storage.googleapis.com/tensorflow/linux/cpu/protobuf-3.1.0-cp35-none-linux_x86_64.whl

ARG tensorflow_version=1.4.1

ENV tf_binary_url=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-${tensorflow_version}-cp35-cp35m-linux_x86_64.whl

# Install Protobuf and TensorFlow CPU version from central repo
RUN pip --no-cache-dir install \
        ${protobuf_url} \
        ${tf_binary_url}

# TensorBoard
EXPOSE 6006
