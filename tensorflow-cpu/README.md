# Using the TensorFlow CPU Container

This directory contains a `Dockerfile` to build an image that contains the
TensorFlow CPU version.  It is based on the `frankhinek/datascience` container
which includes Miniconda, Python 3.5, and a collection of common data science
packages.  It also includes the C++ based protobuf library that is 10x-50x
faster than the Python-only implementation.

## Which containers exist?

Currently I maintain a single TensorFlow Docker container image:

* `frankhinek/tensorflow-cpu` - TensorFlow 1.4.1 and Python 3.5

 This container is published to [Docker Hub](https://hub.docker.com/r/frankhinek/tensorflow-cpu/).

## Running the container

Run the container using

    $ docker run -it frankhinek/tensorflow-cpu

## Rebuilding the containers

Just pick the `Dockerfile` associated with this container, and run:

    $ docker build --pull -t $USER/tensorflow-cpu -f Dockerfile .
