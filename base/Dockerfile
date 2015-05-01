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
#RUN mkdir /goroot && \
#	curl https://storage.googleapis.com/golang/go1.4.linux-amd64.tar.gz | tar xvzf - -C /goroot --strip-components=1
ENV GOLANG_VERSION 1.3

RUN mkdir /goroot && \
	curl -sSL http://golang.org/dl/go$GOLANG_VERSION.src.tar.gz \
        | tar xzvf - -C /goroot --strip-components=1     
WORKDIR /goroot
RUN cd src && ./make.bash --no-clean 2>&1

RUN mkdir /gopath

ENV GOROOT /goroot
ENV GOPATH /gopath
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin
