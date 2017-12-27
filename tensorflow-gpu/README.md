# Using the TensorFlow Container

This repository contains two `Dockerfile` versions for TensorFlow.

The [tensorflow-cpu](https://github.com/frankhinek/containers/tree/master/tensorflow-cpu) version builds an image that contains the TensorFlow CPU version.  It is based on the `frankhinek/datascience` container.

The [tensorflow-gpu](https://github.com/frankhinek/containers/tree/master/tensorflow-gpu) version builds an image that contains TensorFlow with support for NVIDIA GPUs enabled by the CUDA tool kit and accelerated by cuDNN.  It is based on the `nvidia/cuda` container.

Both images include Miniconda, Python 3.5, a collection of common data science packages, and the C++ based protobuf library that is 10x-50x faster than the Python-only implementation.

## Which containers exist?

Currently I maintain two TensorFlow Docker container images:

* `frankhinek/tensorflow:cpu` - TensorFlow 1.4.1 and Python 3.5
* `frankhinek/tensorflow:gpu` - TensorFlow 1.4.1, Python 3.5, CUDA 9.0, and cuDNN 7

These containers are published to [Docker Hub](https://hub.docker.com/r/frankhinek/tensorflow/).

## Running the CPU-only container

Run the container using

    $ docker run -it frankhinek/tensorflow:cpu

## Running the GPU (CUDA) container

Install [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) and run

    $ nvidia-docker run -it frankhinek/tensorflow:gpu

## Rebuilding the containers

Just pick the `Dockerfile` associated with this container, and run:

    $ docker build --pull -t $USER/tensorflow:suffix -f Dockerfile .
