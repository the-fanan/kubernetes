MINIKUBE
==========
This is a tool that allows you to create a single node cluster where master and slave processes are on the same node. This is suitable for setting up and testing clusters on your local machine. It creates the single node in a virtual environment on your machine.

USEFUL COMMANDS
================
- `minikube start` starts your cluster
- `minikube status` get status of cluster
- `minikube service NAME_OF_SERVICE` will assign an external IP to an external service
- `minikube addons enable ingress` setups an ingress controller for your minikube. check the pods in kube-system namespace (`kubectl get pods -n kube-system`) to verify the nginx ingress controller was setup