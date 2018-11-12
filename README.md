# ns-process

Code to accompany the "Namespaces in Go" series of articles.

* [Part 1: Linux Namespaces](https://medium.com/@teddyking/linux-namespaces-850489d3ccf)
* [Part 2: Namespaces in Go - Basics](https://medium.com/@teddyking/namespaces-in-go-basics-e3f0fc1ff69a)
* [Part 3: Namespaces in Go - User](https://medium.com/@teddyking/namespaces-in-go-user-a54ef9476f2a)
* [Part 4: Namespaces in Go - reexec](https://medium.com/@teddyking/namespaces-in-go-reexec-3d1295b91af8)
* [Part 5: Namespaces in Go - Mount](https://medium.com/@teddyking/namespaces-in-go-mount-e4c04fe9fb29)
* [Part 6: Namespaces in Go - Network](https://medium.com/@teddyking/namespaces-in-go-network-fdcf63e76100)
* [Part 7: Namespaces in Go - UTS](https://medium.com/@teddyking/namespaces-in-go-uts-d47aebcdf00e)

## Environment Preparation

For mac users, the simplest way to setup an environment is using Vagrant. 

	vagrant init ubuntu/xenial64
	vagrant up
	vagrant ssh

Install go

	apt install golang-go	

Setup GOPATH

	export GOPATH=$(pwd)

Get extra packages

	go get github.com/docker/docker/pkg/reexec

Build now

	go build	

Install netsetgo

	wget "https://github.com/teddyking/netsetgo/releases/download/0.0.1/netsetgo"
	sudo mv netsetgo /usr/local/bin/
	sudo chown root:root /usr/local/bin/netsetgo
	sudo chmod 4755 /usr/local/bin/netsetgo

Get a root fs

	wget "https://raw.githubusercontent.com/teddyking/ns-process/4.0/assets/busybox.tar"
	mkdir -p /tmp/ns-process/rootfs
	tar -C /tmp/ns-process/rootfs -xf busybox.tar


## Usage

Each of the code extracts in the articles reference a git tag, which can be
checked out from this repo. The code is buildable and runnable at each tag, but
note that it will only run successfully on Linux machines.

## Testing

The test suite isn't explicitly mentioned in the articles, but if you'd like to
run the tests you'll need to install [ginkgo](https://github.com/onsi/ginkgo)
and [gomega](https://github.com/onsi/gomega).  Note that some of the tests may
require root privileges.
