# Rolling Updates and Versioning

> kubectl rollout status deployment/myapp-deployment

> kubectl rollout history deployment/myapp-deployment


There are two type of deployment strategies:
- Recreate strategy: Stop all old pods and creates new ones, there is a gap that your application will be down for some time.
- Rolling update: This strategy does not shuts down all the pods, instead it closes one and creates the new one. It is the default deployment strategy.

> kubectl apply -f deployment-definition.yml

> kubectl set image deployment/myapp-deployment nginx-container=nginx:1.9.1

# Rollback
---
> kubectl rollout history deployment/myapp-deployment

> kubectl rollout undo deployment/myapp-deployment

> kubectl get rs
