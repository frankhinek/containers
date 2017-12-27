# Using the Data Science Container

This directory contains a `Dockerfile` to build an image that can be used for
general data science experiments and projects.

## Which containers exist?

Currently I maintain a single data science Docker container image:

* `frankhinek/datascience` - Miniconda, Python 3.6, and a collection of common packages

 This container is published to [Docker Hub](https://hub.docker.com/r/frankhinek/datascience/).

## Running the container

Run the container using

    $ docker run -it frankhinek/datascience

## Rebuilding the container

Just pick the `Dockerfile` associated with this container, and run:

    $ docker build --pull -t $USER/datascience -f Dockerfile .
