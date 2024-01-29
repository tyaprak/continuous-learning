# Backup and Restoration Methods

## Resource Configs

Tool: VELERO (formerly called ARK by HeptIO)

'''bash

kubectl get all --all-namespaces -o yaml > all-deploy-services.yaml 

'''

## ETCD Backup

Instead of backing up the resources, we may consider backing up etcd as it is the basement of all the configs.

1- ETCD cluster is hosted on the master nodes. In etcd.service file, check ExecStart section to find --data-dir var which is the directory you should backup.
2- etcd comes with a built-in snapshot feature to backup etcd database.

'''bash
etcd snapshot save snapshot.db
etcd snapshot status snapshot.db 
'''

Restoration:

'''bash
systemctl stop kube-apiserver
'''

Restart the etcd cluster and kube-apiserver depends on it.

'''bash
etcdctl snapshot restore snapshot.db --data-dir /var/lib/etcd-from-backup
'''

Then edit etcd.service file ExecStart section, chance --data-dir with the recently created backup folder above /var/lib/etcd-from-backup

'''bash
systemctl daemon-reload
systemctl restart etcd
systemctl start kube-apiserver
'''

DO NOT FORGET:

export ETCDCTL_API=3 && etcdctl snapshot save snapshot.db --endpoints=https://127.0.0.1:2379 --cacert=/etc/etcd/ca.crt --cert=/etc/etcd/etcd-server.crt --key=/etc/etcd/etcd-server.key


--------

# PRACTICE
'''bash
kubectl config get-clusters
kubectl config use-context cluster1
'''