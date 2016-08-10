FROM fedora:23

MAINTAINER Jakub Čajka <jcajka@redhat.com>

#Set up environment
ENV GOPATH=/home/golang/ \
    GOOS=linux \
    GOARCH=amd64

#Install golang
RUN dnf -y install --setopt=tsflags=nodocs golang && dnf clean all

CMD ["go","version"]


