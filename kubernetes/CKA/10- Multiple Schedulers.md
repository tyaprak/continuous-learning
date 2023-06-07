# Multiple Schedulers

> kubectl create configmap --name my-scheduler-config --from-file=/root/my-scheduler-config.yaml -n kube-system 

> kubectl get pods -A
> kubectl describe pod kube-scheduler-controlplane -n kube-system | grep image
- edit the image inside mscheduler-config.yaml file

> kubectl create -f my-scheduler.yaml
> kubectl get pods -n kube-system

```yaml
schedulerName: my-scheduler
```
