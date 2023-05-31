# Taints and Tolerations vs Node Affinity

Taints and Tolerations does not guarantee the deployment of the pod through the correct labeled node.


If you want to deploy red green blue colored pods to red green blue labeled nodes, in case of extra pods exist in the system, combine Taints & Tolerations with Node Affinity to ensure the correct deployment as per you planned.