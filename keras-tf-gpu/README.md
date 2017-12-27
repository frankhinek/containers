# Using the TensorFlow Container

This repository contains two `Dockerfile` versions for Keras with the TensorFlow backend.

The [keras-tf-cpu](https://github.com/frankhinek/containers/tree/master/keras-tf-cpu) version builds an image that contains Keras and the TensorFlow CPU version.  It is based on the `frankhinek/tensorflow:cpu` container.

The [keras-tf-gpu](https://github.com/frankhinek/containers/tree/master/keras-tf-gpu) version builds an image that contains Keras and TensorFlow with support for NVIDIA GPUs enabled by the CUDA tool kit and accelerated by cuDNN.  It is based on the `frankhinek/tensorflow:gpu` container.

Both images include Miniconda, Python 3.5, a collection of common data science packages, and the C++ based protobuf library that is 10x-50x faster than the Python-only implementation.

## Which containers exist?

Currently I maintain two Keras with TensorFlow Docker container images:

* `frankhinek/keras:tf-cpu` - Keras 2.1.2, TensorFlow 1.4.1, and Python 3.5
* `frankhinek/keras:tf-gpu` - Keras 2.1.2, TensorFlow 1.4.1, Python 3.5, CUDA 9.0, and cuDNN 7

These containers are published to [Docker Hub](https://hub.docker.com/r/frankhinek/keras/).

## Running the CPU-only container

Run the container using

    $ docker run -it frankhinek/keras:tf-cpu

## Running the GPU (CUDA) container

Install [nvidia-docker](https://github.com/NVIDIA/nvidia-docker) and run

    $ nvidia-docker run -it frankhinek/keras:tf-gpu

## Rebuilding the containers

Just pick the `Dockerfile` associated with this container, and run:

    $ docker build --pull -t $USER/keras:suffix -f Dockerfile .
