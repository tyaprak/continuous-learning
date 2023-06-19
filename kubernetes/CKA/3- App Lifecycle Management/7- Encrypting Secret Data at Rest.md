# etcdctl must be installed

> apt-get install etcd-client

> ETCDCTL_API=3 etcdctl --cacert=/etc/kubernetes/pki/etcd/ca.crt --cert=/etc/kubernetes/pki/etcd/server.crt --key=/etc/kubernetes/pki/etcd/server.key get registry/secrets/default/my-secret | hexdump -C

Check if the system is already configured to encrypt data at rest

> ps aux | grep kube-api | grep "encryption-provider-service"

or check if encryption-provider-service has alredy been set

> cat /etc/kubernetes/manifests/kube-apiserver.yaml 

> head -c 32 /dev/urandom | base64 # Takes 32-char long data from linuxes random chest.


```yaml
# enc.yaml
apiVersion: apiserver.config.k8s.io/v1
kind: EncryptionConfiguration
resources:
  - resources:
      - secrets
    providers:
      - aescbc:
        - keys:
          - name: key1
            secret: <Output of the last command>
      - identity: {}

```

- Copy this file to /etc/kubernetes/enc, folder name is yours to decide.

- Edit the kube-apiserver.yaml file and add:

Under the commands section:

```yaml
apiVersion:
kind:
.
.
.

spec:
  containers:
  - command:
    - --encryption-provider-config=/etc/kubernetes/enc/enc.yaml

.
.
.

volumeMounts:
  - name: enc
    mountPath: /etc/kubernetes/enc
    readonly: true

.
.
.

volumes:
  - name: enc
    hostPath:
      path: /etc/kubernetes/enc
      type: DirectoryOrCreate
```

