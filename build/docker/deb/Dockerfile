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

RUN apt-get update
RUN wget https://raw.githubusercontent.com/scryptachain/scrypta-os/master/add-apt-repository.sh
RUN mv add-apt-repository.sh /usr/bin/add-apt-repository
RUN chmod +x /usr/bin/add-apt-repository
RUN add-apt-repository -y ppa:bitcoin/bitcoin

RUN apt-get -y install build-essential autoconf automake libtool libboost-all-dev libboost-program-options-dev libssl1.0-dev
RUN apt-get -y install libleveldb-dev libgmp-dev libgmp3-dev libcurl4-openssl-dev libcrypto++-dev libqrencode-dev
RUN apt-get -y install libgmp-dev libssl-dev libcurl4-openssl-dev


ADD build-deb.sh /build/build-deb.sh

WORKDIR /build
