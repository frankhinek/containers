# Using the Kubernetes Debug Container

This directory contains a `Dockerfile` to build an image that can be used for
troubleshooting Kubernetes clusters.

## Which containers exist?

Currently I maintain a single Kubernetes Debug container image:

* `frankhinek/k8s-debug` - Minimal Alpine Linux image with troubleshooting utilities

This container is published to [Docker Hub](https://hub.docker.com/r/frankhinek/k8s-debug/).

## Running the container

Run the container using

    $ kubectl run -it debug --rm --image=frankhinek/k8s-debug --restart=Never

## Rebuilding the container

Just pick the `Dockerfile` associated with this container, and run:

    $ docker build --pull -t $USER/k8s-debug -f Dockerfile .
