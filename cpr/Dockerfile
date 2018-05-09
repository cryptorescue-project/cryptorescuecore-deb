FROM ubuntu:xenial

ENV DEBIAN_FRONTEND noninteractive
ENV HOME /root
ENV TERM linux

RUN apt-get update && \
    apt-get upgrade -qy && \
    apt-get install -qy apt-transport-https curl git && \
    echo 'deb https://deb.nodesource.com/node_10.x xenial main' | tee /etc/apt/sources.list.d/nodesource.list && \
    curl -s https://deb.nodesource.com/gpgkey/nodesource.gpg.key | apt-key add - &&\
    echo 'deb http://ppa.launchpad.net/bitcoin/bitcoin/ubuntu xenial main' | tee -a /etc/apt/sources.list.d/nodesource.list && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8842CE5E
RUN apt-get update && \
    apt-get -qy install nodejs python3 make build-essential devscripts dh-systemd
RUN npm install npm@latest -g
ADD cryptorescuecore/ /root/cryptorescuecore
RUN ( cd /root/cryptorescuecore && debuild -uc -us )
