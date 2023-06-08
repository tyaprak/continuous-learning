# Daemonsets

> kubectl get daemonsets
> kubectl describe daemonsets monitoring-daemon

> kubectl create deployment elasticsearch --image=registry.k82.io/fluentd-elasticsearch:1.20 -n kube-system --dry-run=client -o yaml > fluentd.yaml

delete replicas, status and strategy.

> kubectl create -f fluentd.yaml