> kubectl drain node01 

This command drains all the applications deployed in that node and mark it unscheduleable.
All the pods inside that node evict to another suitable node.

> kubectl uncordon node01 

Sets the node as scheduleable again after the maintenance. After the uncordoning, thee node will be available for the new pods.
Uncordoning does not evict the old pods to that node back.

> kubectl cordon node01