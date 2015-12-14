# docker-fglrx
Dockfile for build AMD fglrx driver. This is the basic images for build AMD APP SDK for OpenCL development.

## Build image
docker build -t halo9pan/fglrx .

## Create container
docker create -t -i --name=fglrx --hostname=ubuntu --device /dev/ati/card0:/dev/ati/card0 halo9pan/fglrx bash

## Start container
docker start -a -i fglrx
