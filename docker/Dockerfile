FROM debian:stretch
LABEL maintainer="obscuraX Developers <dev@obscurax.org>"
LABEL description="Dockerised obscuraXCore, built from Travis"

RUN apt-get update && apt-get -y upgrade && apt-get clean && rm -fr /var/cache/apt/*

COPY bin/* /usr/bin/
