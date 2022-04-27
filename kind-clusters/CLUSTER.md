# K8S CLUSTER MULTNODE
# Using K8S with no fear !

- Create Cluster Manisfest
- Create Cluster
- 
- 

#  Create Cluster Manisfest
```yaml
apiVersion: kind.x-k8s.io/v1alpha4
name: spc-meetup-k8s
nodes:
- role: control-plane
- role: worker
- role: worker
```

# Create Cluster

```sh
kind create cluster --config cluster.yaml
```

- Validate Version

```sh
kubectl version --client
```
```sh
kubectl version --client --output=yaml  
```

# Install a K8S Cluster Creating Tool - (KIND Kubenetes in Docker)
- Download  [KIND](https://kind.sigs.k8s.io/)  binaries. 
```sh
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.12.0/kind-linux-amd64
```
- Set Permission
```sh
chmod +x ./kind
```
- Install KIND CLI
```sh
sudo mv ./kind /usr/local/bin/
```
# Creating a K8S Mono Cluster
- Verify Docker Deamon
```sh
sudo /etc/init.d/docker start
```
- Create a K8S Mono Cluster with KIND
```sh
kind create cluster --name=mono
```
# Setting Kubectl Cluster Context 
```sh
kubectl cluster-info --context kind-mono
```
==============================
### Interacting With Your Cluster
- List Clusters
 ```sh
  kind get clusters
 ```
- Delete a Cluster
```sh
kind delete cluster --name=mono
```
- Get  a Nodes
```sh
kind get nodes
```
=================================================

# Creating Resources

# PODs, Deployments, Services, etc
```sh
kubectl apply -f pod.yaml
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml 
```

# Redirect to a POD
```sh 
kubectl port-forward pod/numeros-por-extenso 8888:80
```
```sh 
# http://localhost:8888/conversor/por-extenso/
```
# Redirect to a SERVICE
```sh 
kubectl port-forward service/numeros-por-extenso-service 8081:https
```


