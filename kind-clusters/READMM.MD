# FERRAMENTA DE CRIAÇÃO DE CLUSTERS K8S EM {DEV}
curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.12.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/

# INTALL KUBECTRL - FERRAMENTA DE INTERAÇÃO COM OS CLUSTERS
	#1 INSTALAR OS BINARIOS 
	curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
	#2 INTALL KUBECTRL - FERRAMENTA DE INTERAÇÃO COM OS CLUSTERS
	sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
	#3 VALIDANDO VERSÃO DO kubectl
	kubectl version --client
	kubectl version --client --output=yaml   
	

=============================================	

#CREATE MONO CLUSTER
kind create cluster --name=mono

#DELETE MONO CLUSTER
kind delete cluster --name=mono

#LISTANDO CLUSTERS
kind get clusters

=================================

# SETANDO O CONTEXTO PARA O NOVO CLUSTER
 kubectl cluster-info --context kind-mono

# VERIFICANDO NODES DO CLUSTER
kubectl get nodes

# CRIADO UM POD 
kubectl apply -f Pod.yaml

# LISTANDO PODS
kubectl get pods

# ACESSADNO O POD LOCALMENTE
kubectl port-forward pod/numeros-por-extenso 8888:80
# http://localhost:8888/conversor/por-extenso/


kubectl port-forward service/numeros-por-extenso-service 8081:https

#Multicluster  

# PODEMOS CRIAR UM CLUSTER COM 6 nodes
# a cluster with 3 control-plane nodes and 3 workers
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
- role: control-plane
- role: control-plane
- role: control-plane
- role: worker
- role: worker
- role: worker

