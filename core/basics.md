NODE
=======
Simples server. Can be a physical or virtual machine.

POD
======
An abstraction over a container. This is done so as to "separate" container from the Node. This allows for easy use of whatever kind container you want. Whether Docker or Rkt. A Pod is usually meant to run only one container inside of it even though it can run multiple containers. Multiple pods can however be on the same node. Kubernetes comes with it's own virtual network so every pod (not container) has it's own IP address.

SERVICE
==========
When pods die or restart, their IP addresses change. To mitigate that, a service comes in. Service is a permanent IP address that can be attached to each pod. Services can be **External** or **Internal**. External is open to world, internal is only open to pods and other services withing the Kubernetes network. Service can be shared between two or more Nodes. This is because they also act as a load balancer.

INGRESS
===========
Services only grant IPs and are usually linked to a port. Ingress provides a friendly user facing URL that links the external world to your external services.

CONFIG MAP
============
Contains configuration data like URLs and other environment variables so that they can be easily udated without having to rebuild, pull images, and restart pods/containers for minor updates.

SECRET
===========
Passwords and other autentication data cannot (AND SHOULD NOT) be stored in the Config Map as it is not encrypted. Secret enables you to store sensitive data. It's like the config map but for secret information.

VOLUMES
===========
The storage in pods are temporary and get wiped if the pod dies or restarts. Volumes allow you to attach a more permanent storage medium to your pod. This can be a local (within the Kubernetes cluster) or cloud storage.

DEPLOYMENT
============
This is an abstraction over pods. They make it more convienient to work with pods and other K8s components. However, deployment can only replicate stateless pods.

STAETFUL SET
============
This is like Deployment but for Stateful pods. However, it is way more stressful to work with Stateful Set than to work with Deployments.


REPLICA SET
================
This is responsible for creating multiple copies of a pod across nodes. You never have to interact directly with it, the Deployment automatically configures the replicaset for you.