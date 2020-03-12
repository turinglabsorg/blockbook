# initialize from the image

FROM blockbook-build:latest

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y devscripts debhelper make dh-systemd dh-exec && \
    apt-get clean

ADD gpg-keys /tmp/gpg-keys
RUN gpg --batch --import /tmp/gpg-keys/*

# Scrypta depenencies
RUN apt-get install -y software-properties-common 

RUN add-apt-repository -y ppa:bitcoin/bitcoin

RUN apt-get update

RUN apt-get install -y libdb4.8 libdb4.8++ wget libboost1.58-all libminiupnpc10

ADD build-deb.sh /build/build-deb.sh

WORKDIR /build
