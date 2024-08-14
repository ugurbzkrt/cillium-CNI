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
