#
# docker run -ti --rm --device=/dev/ttyUSB0:/dev/ttyUSB0 -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix linuxluser/chirp
#

FROM ubuntu:bionic
LABEL maintainer="Matthew L. Shields"
LABEL maintainer.email="geek@shields.cc"


RUN apt-get update \
    && apt-get install -y \
        apt-transport-https \
        software-properties-common \
        gnupg \
        curl \
        ca-certificates \
        --no-install-recommends \
	    && rm -rf /var/lib/apt/lists/*

RUN add-apt-repository ppa:dansmith/chirp-snapshots \
    && apt-get update \
    && apt-get install -y \
        chirp-daily

ENTRYPOINT [ "/usr/bin/chirpw" ]