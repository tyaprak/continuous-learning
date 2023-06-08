# Node Affinity

To accomplish complex node selection tasks, using node affinity is the way.

```yaml
apiVersion:
kind:

metadata:
  name:
spec:
  containers:
   - name: data-processor
     image: data-processor
  
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: size
            operator: In
            values:
            - Large
          - key: size
            operator: Exists # this operator only checks if size key exists in node labels
```

Available:
- requiredDuringSchedulingIgnoredDuringExecution
- preferredDuringSchedulingIgnoredDuringExecution

Planned:
- requiredDuringSchedulingRequiredDuringExecution
- preferredDuringSchedulingRequiredDuringExecution