```
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

helm repo add cilium https://helm.cilium.io/
helm repo update

helm install cilium cilium/cilium --namespace kube-system


kubectl -n kube-system get pods -l k8s-app=cilium
kubectl get pods -A
```
