# Static PODs
---

Important information to check static pods:

> kubelet.service
>> --config=kubeconfig.yaml or --staticPodPath=/etc/kubernetes/manifests



> kubeconfig.yaml
>> staticPodPath: /etc/kubernetes/manifests

- Check on which node the pod is running
> ssh node01
>> ps aux | grep kubelet

Find "--config=" part and cat the config file, grep **staticPodPath**

on the node01, greenbox.yaml file was located under /etc/just-messing-with-you/ folder. Delete that yaml file and you will get rid of static-greenbox pod working on node01.

Note that a static pods kind will be:
ownerReferences:
- kind: Node
