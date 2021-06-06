KUBECTL
============
This is a command line tool for communicating with your K8s cluster.


USEFUL COMMANDS
================
- `kubectl get nodes` OR `kubectl get node` gets status of nodes
- `kubectl get pods` OR `kubectl get pod` gets status of pods
- `kubectl get services` OR `kubectl get service` gets status of services
- `kubectl get ingresses` OR `kubectl get ingress` gets status of ingresses
- `kubectl get deployments` OR `kubectl get deployment` gets status of deployments
- `kubectl get statefulsets` OR `kubectl get statefulset` gets status of statefulsets
- `kubectl get secret` OR  `kubectl get secrets` gets status of secret
- `kubectl get replicaset` get status of replicasets
- `kubectl create deployment {NAME_OF_DEPLOYMENT} --image={SOURCE_OF_IMAGE}` create a deployment
- `kubectl create -f PATH_TO_CONFIG_FILE` create a pod from a YAML or JSON file
- `kubectl logs {POD_NAME}` shows you what an application in the pod logged
- `kubectl describe pod {POD_NAME}` shows you state changes going on in the pod
- `kubectl exec -it {POD_NAME} -- bin/bash` logs you into the interactive terminal of a pod
- `kubectl apply -f PATH_TO_CONFIG_FILE` creates all the components stated in the file and creates a cluster from that
- You can run `kubectl [...] -h` to get more info on commands and their optional arguments