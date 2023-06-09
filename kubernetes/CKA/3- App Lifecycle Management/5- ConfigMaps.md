# ConfigMaps

ConfigMaps stored as key: value pairs.

1- Create the configMap
2- Inject it into the pod.


Two ways to create a configmap:

Imperative:
> kubectl create configmap app-config --from-literal=APP_COLOR=blue --from-literal=APP_MODE=prod ... 
                                      --from-file=app_config.properties

Declerative:
> kubectl create -f 


```yaml
#config-map.yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_COLOR: blue
  APP_MODE: prod
  .
  .
  .
```

> kubectl create -f config-map.yaml


EXAMPLES of usage:

```yaml
# mysql-config
port: 3306
max_allowed_packet: 128M
```


```yaml
# redis-config
port: 6379
rdb-compression: yes
```

> kubectl get configmaps

> kubectl describe configmaps

---

# POD with ENV vars

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: simple-webapp
  labels:
    name: simple-webapp
spec:
  containers:
  - name: simple-webapp
    image: simple-webapp
    ports:
      - containerPort: 8080
    envFrom:
      - configMapRef:
            name: app-config

```