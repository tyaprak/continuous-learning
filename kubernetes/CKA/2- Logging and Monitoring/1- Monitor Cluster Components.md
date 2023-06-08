# Monitor Cluster Components

- Heapster (deprecated)
- Metrics Server

If you are using minikube:
> minikube addons enable metrics-server

for all others:

> git clone https://github.com/kubernetes-incubator/metrics-serve
> kubectl create -f deploy/1.8+/

> kubectl top node
> kubectl top pod
