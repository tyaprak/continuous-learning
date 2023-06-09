# Secrets

Secrets are like configmap, but sensitive information must be stored encrypted.

Again, imperative and declerative ways to create.

Imperative:

> kubectl crate secret generic <secret-name> --from-literal=<key>=<value>
>>                                           --from-file=



Declerative:

```yaml
#secret-data.yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
data:
  DB_Host: mysql 
  DB_User: root
  DB_Password: passwrd
```

> kubectl create -f secret-data.yaml

In the yaml file, secrets must be base64 encoded. 

Instead of typing "mysql" in cleartext format, you must store the output of the following command

> echo -n "mysql" | base64

How to get the secrets?

> kubectl get secret app-secret -o yaml


# How to use secrets within the pods?

```yaml
#pod-definition.yaml

apiVersion: v1
kind: Pod
metadata:
  name: simple-app
  labels:
    name: simple-app
spec:
  containers:
  - name: simple-app
    image: simple-app
    ports:
      - containerPort: 8080
    envFrom:
      - secretRef:
            name: secret-data
```

OR

```yaml
.
.
.

env:
  - name: DB_Password
    valueFrom:
        secretKeyRef:
            name: app-secret
            key: DB_Password
```

OR

```yaml
.
.
.

volumes:
- name: app-secret-volume
  secret:
    secretName: app-secret
```


Remember:
- Secrets are not encrypted, they are encoded.
- Do not check in your secret objects to SCM along with the code, add them to .gitignore file
- Secrets are not encrypted in etcd, consider enabling encryption at rest.
- Consider privilege management as anyone able to create pods/deployments in the same namespace can access the secrets.
- Consider storing the secrets in a third-party environment.