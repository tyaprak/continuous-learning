Taints and Tolerations
---

> kubectl taint node node01 spray=mortein:NoSchedule

> kubectl describe node node01 | grep aint

> kubectl run mosquito --image nginx
>> kubectl describe pod mosquito --> taint {spray:mortein} cannot be tolarated!

> kubectl run bee --image nginx --dry-run=client -o yaml > bee.yaml

>> vi bee.yaml

>> Under spec create toleration

```yaml
tolerations:
- key: spray
  operator: Equal
  value: mortein
  effect: NoSchedule
```
>> kubectl apply -f bee.yaml


> kubectl get pods --watch
> kubectl edit node controlplane --> Remove the Taints
> or
> kubectl taint node controlplane node-role.kubernetes.io/master:NoSchedule- 

The dash (-) at the end is untainting the node controlplane which will allow "Pending" pods to *run*.
