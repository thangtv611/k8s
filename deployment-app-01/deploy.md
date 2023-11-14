# Example
## Example 1
### Create a new deployments
- A deployment checks on the health of Pod and restart if the Pod terminates
- A deployment used to manage the creation and replication of Pods
```
kubectl create deployment hello-node --image=registry.k8s.io/e2e-test-images/agnhost:2.39 -- /agnhost netexec --http-port=8080
```
### Expose the Pod
- By default, Pod can be accessbile by its internal IP address with the k8s cluster.
- To make Pod visible outside of k8s cluster, need to expose the Pod as k8s `service`
```
kubectl expose deployment hello-node --type=LoadBalancer --port=8080
```
- Some of Cloud Provider provides Load Balancer, once exposing deployment, a Cloud Load Balancer will attach to External IP of the service
- To expose external IP in minikube, should run the command:
```
minikube service <service_name>
```
# Concern
1. What is the relationship of `Deployment` and `ReplicaSet`?