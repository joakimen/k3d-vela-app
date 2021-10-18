# k3d-vela-app

Example app using k3d and KubeVela

## Requirements

* k3d >= 1.18.0 (or any other available Kubernetes-cluster)
* kubectl
* Helm 3

## Setup

### Create Kubernetes-cluster

```bash
$ k3d cluster create vela-demo --image rancher/k3s:v1.18.20-k3s1
INFO[0000] Prep: Network                                
INFO[0000] Created network 'k3d-vela-demo'              
INFO[0000] Created volume 'k3d-vela-demo-images'
...
```

### Install the KubeVela Helm Chart

```bash
$ helm repo add kubevela https://charts.kubevela.net/core

"kubevela" has been added to your repositories

$ helm repo update
Hang tight while we grab the latest from your chart repositories...
...Successfully got an update from the "kubevela" chart repository
Update Complete. ⎈Happy Helming!⎈

$ helm install kubevela kubevela/vela-core \
    --create-namespace -n vela-system \
    --set multicluster.enabled=true \
    --wait

```

### Install the `vela` -binary for convenience

Download a release from https://github.com/oam-dev/kubevela/releases

```bash
$ curl -sSL https://github.com/oam-dev/kubevela/releases/download/v1.1.5/vela-v1.1.5-linux-amd64.tar.gz | tar -xvz
linux-amd64/
linux-amd64/README.md
linux-amd64/LICENSE
linux-amd64/vela

$ mv linux-amd64/vela .

```
