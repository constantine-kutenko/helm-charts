# nfs-provisioner

## Prerequisites

In order to run provisioner on a certain node that node should be labeled and its role and taint should be set. For example if a node has name `k8s-worker-01` and its role is `storage` the respective commands will look like:

```bash
kubectl label node k8s-worker-01 node-role.kubernetes.io/storage=
kubectl taint nodes k8s-worker-01 node-role.kubernetes.io/storage=:NoSchedule
```

## Install the chart

```bash
helm install \
    --name nfs-provisioner \
    --namespace kube-system \
    --set environment=production \
    nfs-provisioner
```

## Verify the installation

```bash
helm list | grep nfs-provisioner
```
