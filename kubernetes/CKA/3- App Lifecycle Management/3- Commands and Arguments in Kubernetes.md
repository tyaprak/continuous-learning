
## Lets use the container we created, named **ubuntu-sleeper** to create a **kubernetes pod**
---


````yaml
apiVersion: v1
kind: Pod
metadata:
  name: ubuntu-sleeper-pod
spec:
  containers:
    - name: ubuntu-sleeper
      image: ubuntu-sleeper
      command: ["sleep2.0"] 
      args: ["10"]
```

REMEMBER: commands and args **OVERRIDE** the config in docker file.

> kubectl create -f pod-definition.yaml

> kubectl replace --force -f /tmp/kubectl-edit-12352342.yaml

> kubectl run webapp-green --image=kk/webapp-color -- --color green  # Double dashes represents (python3 app.py)