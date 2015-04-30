FROM resin/rpi-raspbian:wheezy
MAINTAINER m.nieberg@gmx.de

RUN apt-get update -y && \
    apt-get install --no-install-recommends -y -q \
	build-essential \
	bzr \
	ca-certificates \
	curl \
	git \
	mercurial
RUN mkdir /goroot && \
	curl https://storage.googleapis.com/golang/go1.4.linux-amd64.tar.gz | tar xvzf - -C /goroot --strip-components=1
RUN mkdir /gopath

ENV GOROOT /goroot
ENV GOPATH /gopath
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin
