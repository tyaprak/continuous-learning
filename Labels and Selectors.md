# Labels & Selectors

- Get all objects (pods, replicasets, services) labeled as prod env.
> kubectl get all --selector env=prod

- Get all production environment pods and objects without headers
> kubectl get pod --selector env=prod --no-headers
> kubectl get all --selector env=prod --no-headers

- Multiple filtering
> kubectl get all --selector env=prod,bu=finance,tier=frontend

_ REMEMBER _
===========
**matchLabel** is the most important value in the yaml file in order a replicaset to match with the relevant pods.