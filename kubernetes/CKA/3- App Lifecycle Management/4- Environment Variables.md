# Environment Value Types

There are 3 types of ENV value set:

1- Plain Key-Value
2- ConfigMap
3- Secrets


For plain key-value:

```yaml
env:
  - name: APP_COLOR
    value: red
```

for configMap

```yaml
env:
  - name: APP_COLOR
    valuefrom: 
        configMapKeyRef:
```


for Secrets:

```yaml
env:
  - name: APP_COLOR
    valuefrom: 
        secretKeyRef:
```