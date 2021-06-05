PODS
=====
Hold containers

NODES
=======
Hold ports, they are the machines

KUBELETS
=========
Launch pods

KUBE-PROXY
===========
Feed ip-tables about what pods are on a node

IP TABLES
=============
Linux firewall, they route traffic

SERVICE
===========
Usually a load balacer. e.g. AWS ELB 

STATELESS PODS
=================
pods that do not keep local files or store sessions locally.

REPLICATION CONTROLLER
=======================
used to scale apps. can replicate multiple versions of a stateless pod and ensure specified number of replicas are running