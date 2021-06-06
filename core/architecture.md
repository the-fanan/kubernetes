SLAVE NODES
=============
These are nodes that do the actual work of hosting the pods. Slave Nodes require three processes for them to execute properly.

1. Container runtime (i.e. Docker or Rkt)
2. Kubelet
3. Kube Proxy

KUBELET
===========
This acts as an interface between the container runtime and the node. It is responsible for starting the pod and allocating resources to pods.

KUBE PROXY
==============
This forwards requests between nodes and services.

MASTER NODES
==============
Master nodes control all the other processes on the slave nodes. The Master nodes have four services (different from the three services on the slave) that must be running:

1. **API Server**: This is a gateway and gatekeeper for authentication. This is responsible for controlling cluster deployments and can be communicated to either via a UI interface or command line like Kubectl or some K8s API.
2. **Scheduler**: The API server delegates creation of pods on slave nodes to a scheduler. The scheduler then selects the node on which the pod should be scheduled. It is the Kubelet on the slave node that does the actual creation.
3. **Controller Manager**: Detects changes in the state of slave nodes (like a pod crashing) and tries to ensure the state remains the same.
4. **Etcd**: Key-value store of the cluster state. Basically stores every change in the cluster. This is how the **CM** knows when a pod has crashed and how a **Scheduler** know what pods need scheduling. It does not store application data (e.g. files, databases etc.)

A cluster can have multiple master nodes and they will be load balanced.