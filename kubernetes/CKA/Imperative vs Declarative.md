# **Exam Tips**

## Create objects

### Declerative
> kubectl apply -f nginx.yaml

### Imperative

> kubectl run --image=nginx nginx

> kubectl create deployment --image=nginx nginx

> kubectl expose deployment nginx --port 80

## Update objects

### Declerative

> kubectl apply -f nginx.yaml

### Imperative

> kubectl edit deployment nginx

> kubectl scale deployment nginx --replicas=5

> kubectl set image deployment nginx nginx=nginx:1.18

---

> Generate POD Manifest YAML file (-o yaml). Don’t create it(–dry-run)

>> kubectl run nginx --image=nginx --dry-run=client -o yaml



> Generate Deployment YAML file (-o yaml). Don’t create it(–dry-run)

>> kubectl create deployment --image=nginx nginx --dry-run=client -o yaml



> kubectl create deployment nginx --image=nginx --dry-run=client -o yaml > nginx-deployment.yaml


# Service

> Create a Service named redis-service of type ClusterIP to expose pod redis on port 6379

>> kubectl expose pod redis --port=6379 --name redis-service --dry-run=client -o yaml

>> or

>> kubectl create service clusterip redis --tcp=6379:6379 --dry-run=client -o yaml



> Create a Service named nginx of type NodePort to expose pod nginx’s port 80 on port 30080 on the nodes:
>> kubectl expose pod nginx --type=NodePort --port=80 --name=nginx-service --dry-run=client -o yaml

>> or 

>> kubectl create service nodeport nginx --tcp=80:80 --node-port=30080 --dry-run=client -o yaml
