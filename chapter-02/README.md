# 2.2
```console
❯ kubectl version
Client Version: v1.32.0
Kustomize Version: v5.5.0
The connection to the server localhost:8080 was refused - did you specify the right host or port?

❯ kind version
kind v0.26.0 go1.23.4 linux/amd64

❯ kind create cluster --image=kindest/node:v1.29.0
Creating cluster "kind" ...
 ✓ Ensuring node image (kindest/node:v1.29.0) 🖼
 ✓ Preparing nodes 📦
 ✓ Writing configuration 📜
 ✓ Starting control-plane 🕹️
 ✓ Installing CNI 🔌
 ✓ Installing StorageClass 💾
Set kubectl context to "kind-kind"
You can now use your cluster with:

kubectl cluster-info --context kind-kind

Thanks for using kind! 😊

❯ kubectl cluster-info --context kind-kind
Kubernetes control plane is running at https://127.0.0.1:33537
CoreDNS is running at https://127.0.0.1:33537/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.

❯ kubectl get nodes
NAME                 STATUS   ROLES           AGE     VERSION
kind-control-plane   Ready    control-plane   3m25s   v1.29.0

❯ kind delete cluster
Deleting cluster "kind" ...
Deleted nodes: ["kind-control-plane"]

❯ kubectl cluster-info --context kind-kind
error: context "kind-kind" does not exist
```
