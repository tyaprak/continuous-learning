# Node Selector

If you have nodes with different specs, you may want to deploy your pods accordingly.

In the pod-definition.yaml file simply add:

```yaml
nodeSelector:
    size: Large
```
  
How does kubernetes know if a node is large or not? 
- Kubernetes checks the labels of the nodes, these key-value pairs must be assigned during creation of the node.
> kubectl label node node01 size=Large

Now when you create the pod-definition.yaml it would be deployed on node01.

This only supports node selection, but if you have a complex wish for a pod to deploy like (Large or Medium) or (NOT Small) then nodeSelector will not solve your problem. 
For that, check Node Affinity