# Resource Limits

````yaml
apiVersion: v1
kind: Pod
metadata:
  name: simple-webapp
  labels:
    name: simple-webapp
spec:
  containers:
  - name: simple-webapp
    image: simple-webapp-color
    ports:
      - containerPort: 8080
      
    resources:
      requests:
        memory: "1Gi"
        cpu: 1
      
      limits:
        memory: "2Gi"
        cpu: 2

```

LimitRange -> a kind of kinds. Limits will take effect on newly created pods.

```yaml
spec:
  limits:
  - default:
      cpu: 500m
    defaultRequest:
      cpu: 500m
    max:
      cpu: "1" 
    min:
      cpu: 100m
    type: Container
```
ResourceQuota -> also a kind of kinds.