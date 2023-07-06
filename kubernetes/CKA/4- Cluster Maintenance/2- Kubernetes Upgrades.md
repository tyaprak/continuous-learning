# Kubernetes Upgrades

> kubeadm upgrade plan

- Remote version is the latest version.

> kubectl drain controlplain --ignore-daemonsets

> kubectl cordon controlplain

- controlplane node is drained and tagged as Unschedulable

> apt-get upgrade

---

# Node01

> apt-get update

> apt-get install kubeadm=1.27.0-00

> kubeadm upgrade node

> apt-get install kubelet=1.27.0-00

> systemctl daemon-reload

> systemctl restart kubelet 


# Controlplane

> kubectl get nodes 

Check if both nodes are upgraded to version 1.27.0 !