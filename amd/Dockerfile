# Start with build pack dependencies trusty image
FROM buildpack-deps:trusty
MAINTAINER Halo9Pan <halo9pan@gmail.com>

# RUN sed -i 's/http:\/\/archive\.ubuntu\.com/http:\/\/mirrors\.yun-idc\.com/g' /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
  build-essential unzip \
  cdbs fakeroot execstack dh-modaliases dkms \
  lib32gcc1 libc6-i386 \
  linux-headers-generic
# linux-headers-3.19.0-32-generic

RUN cd /tmp && \
  wget -q http://www2.ati.com/drivers/linux/amd-catalyst-15.9-linux-installer-15.201.1151-x86.x86_64.zip 

# COPY amd-catalyst-15.9-linux-installer-15.201.1151-x86.x86_64.zip /tmp/

RUN cd /tmp && \
  unzip amd-catalyst-15.9-linux-installer-15.201.1151-x86.x86_64.zip && \
  chmod +x AMD-Catalyst-*.run && \
  ./AMD-Catalyst-15.9-Linux-installer-15.201.1151-x86.x86_64.run --buildpkg Ubuntu/trusty --NoXServer

RUN cd /tmp && \
# dpkg -i fglrx_15.201-0ubuntu1_amd64.deb && \
# dpkg -i fglrx-dev_15.201-0ubuntu1_amd64.deb && \
# dpkg -i fglrx-amdcccle_15.201-0ubuntu1_amd64.deb && \
  dpkg -i fglrx-core_15.201-0ubuntu1_amd64.deb

RUN rm -rf fglrx_* fglrx-* AMD-Catalyst-*.run amd-catalyst-*.zip
