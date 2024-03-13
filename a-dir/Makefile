

IMG := myetcd:v3.5.1

GOOS := linux
GOARCH := amd64
export GOOS
export GOARCH

build:
	cd ../ && make KUBE_BUILD_PLATFORMS=linux/amd64 build

docker:
	cp Dockerfile ../bin/
	cd ../bin/ && docker build -f Dockerfile -t ${IMG} .

scpyaml:
	-ssh l 'rm -f /etc/kubernetes/manifests/etcd.yaml'
	sleep 5
	scp etcd.yaml l:/etc/kubernetes/manifests/etcd.yaml


all: build docker scpyaml
	@echo "all"
