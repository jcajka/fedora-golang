# fedora-golang
Dockerfiles for Fedora based images with golang

## Tag overview

| Fedora release  | Go version | Tag |
| ------------- | ------------- | ------------- |
| Fedora 25  | go1.7.3  | 25, latest|
| Fedora 24  | go1.6.3  | 24 |
| Fedora 23  | go1.5.4  | 23 |
| Fedora 24  | go1.7.3  | 24-go1.7 |
| Fedora 23  | go1.7.3  | 23-go1.7 |
| Fedora 25  | go-devel | 25-tip | 
| Fedora 24  | go-devel | 24-tip |
| Fedora 23  | go-devel | 23-tip |

Go1.7 is obtained from https://copr.fedorainfracloud.org/coprs/jcajka/golang1.7/
Go-devel is obtained from https://copr.fedorainfracloud.org/coprs/jcajka/golang-rawhide/

## Basic usage

Directly running the container will output version of the pre-installed go compiler.

For example building etcd by bind mounting the source(GOPATH) directory in to the container and putting resulting binary in to separate bind mounted output directory.

```bash
mkdir -p /home/user/etcd-path
mkdir -p /home/user/etcd-bin
GOPATH=/home/user/etcd-gopath go get -d github.com/coreos/etcd
sudo docker run --env=GOPATH=/gopath --volume=/home/user/etcd-gopath:/gopath:Z --volume=/home/user/tmp/etcd-bin:/gobin:Z jcajka/fedora-golang:24-go1.7 go build -o /gobin/etcd github.com/coreos/etcd
```

Note: Adjust paths accordingly to your environment.

-----

PS: It is awesome as docker hub is always using this file, for the corresponding docker hub repo description. Even when the description were manually edited in docker hub web UI... :/
