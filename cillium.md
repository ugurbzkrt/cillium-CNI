# Installation

```
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

helm repo add cilium https://helm.cilium.io/
helm repo update

helm install cilium cilium/cilium --namespace kube-system


kubectl -n kube-system get pods -l k8s-app=cilium
kubectl get pods -A
```


## Plus

$ cilium status --wait


- Run the following command to validate that your cluster has proper network connectivity:

$ cilium connectivity test

### Enable Hubble

- Hubble is the observability layer of Cilium and can be used to obtain cluster-wide visibility into the network and security layer of your Kubernetes cluster.

$ cilium hubble enable

- Run cilium status to validate that Hubble is enabled and running:

$ cilium status

```
    /¯¯\
 /¯¯\__/¯¯\    Cilium:         OK
 \__/¯¯\__/    Operator:       OK
 /¯¯\__/¯¯\    Hubble:         OK
 \__/¯¯\__/    ClusterMesh:    disabled
    \__/
```

- Hubble CLI

```
HUBBLE_VERSION=$(curl -s https://raw.githubusercontent.com/cilium/hubble/master/stable.txt)
HUBBLE_ARCH=amd64
if [ "$(uname -m)" = "aarch64" ]; then HUBBLE_ARCH=arm64; fi
curl -L --fail --remote-name-all https://github.com/cilium/hubble/releases/download/$HUBBLE_VERSION/hubble-linux-${HUBBLE_ARCH}.tar.gz{,.sha256sum}
sha256sum --check hubble-linux-${HUBBLE_ARCH}.tar.gz.sha256sum
sudo tar xzvfC hubble-linux-${HUBBLE_ARCH}.tar.gz /usr/local/bin
rm hubble-linux-${HUBBLE_ARCH}.tar.gz{,.sha256sum}
```

$ hubble status

- You can also query the flow API and look for flows:

$ hubble observe
