### install k3s with metal
https://oneuptime.com/blog/post/2026-01-07-metallb-k3s-lightweight-kubernetes/view
curl -sfL https://get.k3s.io | INSTALL_K3S_EXEC="--disable servicelb" sh -

setup kubectl
on host fix permissions
sudo chmod 644 /etc/rancher/k3s/k3s.yaml

copy config
scp kadin@10.10.10.228:/etc/rancher/k3s/k3s.yaml ~/.kube/config
fix ip in config
sed -i '' 's/127.0.0.1/10.10.10.228/g' ~/.kube/config

verify installed correctly and can access
❯ kubectl get nodes
verify lb disabled (should return nothign)
kubectl get pods -n kube-system | grep svclb

## install metalLb
lookup how to do this

apply ip pools
## install argocd
https://argo-cd.readthedocs.io/en/stable/getting_started/
#### patch argocd to use load balancer