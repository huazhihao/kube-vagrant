# kube-vagrant

[![Build Status](https://travis-ci.org/huazhihao/kube-vagrant.svg?branch=master)](https://travis-ci.org/huazhihao/kube-vagrant)
![Proudly written in Bash](https://img.shields.io/badge/written%20in-bash-ff69b4.svg)
[![LICENSE](https://img.shields.io/github/license/huazhihao/kube-vagrant.svg)](https://github.com/huazhihao/kube-vagrant/blob/master/LICENSE)
[![Releases](https://img.shields.io/github/v/release/huazhihao/kube-vagrant.svg)](https://github.com/huazhihao/kube-vagrant/releases)

`kube-vagrant` is a kubectl plugin to create a multi-node kubernetes cluster locally with vagrant (usually for development purpose).


## Installation

### Install from source

```sh
$ curl -so kubectl-vagrant https://raw.githubusercontent.com/huazhihao/kube-vagrant/master/kube-vagrant
$ sudo install kubectl-vagrant /usr/local/bin/
```

## Usage

```sh
# create a cluster with default settings (3 nodes with 2GB mem each)
$ kubectl vagrant up

# create a cluster with a subnet "192.168.0.0/16" as pod network cidr
$ kubectl vagrant up --pod-network-cidr="192.168.0.0/16"

# create a cluster with 1 master node and 2 worker nodes
$ kubectl vagrant up --master-node-count=1 --worker-node-count=2

# create a cluster with master node given 2048Mb memory and worker node given
# 2048Mb memory
$ kubectl vagrant up --master-node-memory=2048 --worker-node-memory=2048

# create a cluster with public network bridged by nic "en0: Wi-Fi (AirPort)"
$ kubectl vagrant up --public-network-bridge="en0: Wi-Fi (AirPort)"
```

The kube config yaml file will be saved to `.kube/config`

```sh
$ kubectl --kubeconfig=.kube/config  cluster-info
```

To suspend or destroy the cluster created under the current directory,

```sh
# suspend the vagrant VMs for the cluster created under the current directory
$ kubectl vagrant suspend

# destroy the vagrant VMs for the cluster created under the current directory
$ kubectl vagrant destroy
```

## Demo

[![asciicast](https://asciinema.org/a/T2zS0kTcZkp31zOfSgAo4G95s.svg)](https://asciinema.org/a/T2zS0kTcZkp31zOfSgAo4G95s)
