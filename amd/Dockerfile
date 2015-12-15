# Start with build pack dependencies trusty image
FROM halo9pan/fglrx
MAINTAINER Halo9Pan <halo9pan@gmail.com>

RUN apt-get install -y \
  libqtcore4 libxfixes3 libxrandr2 qtcore4-l10n

ENV FGLRX_VERSION=15.300-0ubuntu1_amd64_UB_14.01

RUN cd /tmp && \
  wget -q http://www2.ati.com/drivers/linux/fglrx_${FGLRX_VERSION}.deb && \
  wget -q http://www2.ati.com/drivers/linux/fglrx-dev_${FGLRX_VERSION}.deb

# RUN cd /tmp && \
# wget -q http://www2.ati.com/drivers/linux/radeon-crimson-15.11-15.30.1025.zip && \
# unzip radeon-crimson-15.11-15.30.1025.zip && cd fglrx-15.30.1025 && \
# chmod +x amd-driver-installer-*.run && \
# ./amd-driver-installer-15.30.1025-x86.x86_64.run --buildpkg Ubuntu/trusty --NoXServer

RUN cd /tmp && \
  dpkg -i fglrx-*.deb && \
  dpkg -i fglrx_*.deb

RUN rm -rf fglrx_* fglrx-*

ADD AMD-APP-SDKInstaller-v3.0.130.135-GA-linux64.tar.bz2 /tmp/

RUN cd /tmp && \
  tar -xjf AMD-APP-SDKInstaller-v3.0.130.135-GA-linux64.tar.bz2 && \
  chmod +x AMD-APP-SDK-*.sh && \
  ./AMD-APP-SDK-v3.0.130.135-GA-linux64.sh -- --acceptEULA 'yes' -s

RUN clinfo

