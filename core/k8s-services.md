KUBERNETES SERVICES
=====================
This is an in-depth explanation of differents services and their uses. 

## Types Of Services

### ClusterIP
This is the default serivce type. It is used to grant persistent IP addresses within a cluster.

### Headless Services
This is used for stateful applications where pod replicas are not identical. You can make a service a headless service by setting the *spec*  **clusterIP** to `None`.

### NodePort
Creates a service that has a static port on each worker node of a cluster. This makes the service accessible to external traffic. You can make a clusterIP service to be a nodePort service by setting *spec* **type** to `NodePort` and *ports* **NodePort** to a range between `30000` to `326767`.

### LoadBalancer
Service is accessible externally through a cloud provider's LoadBalancer.
You can make a clusterIP service to be a LoadBalancer service by setting *spec* **type** to `LoadBalancer` and *ports* **NodePort** to a range between `30000` to `326767`.
sample.yaml
---
apiVersion: v1
kind: Service
metadata:
  name: loadbalancer-service 
spec:
  selector:
    app: mongo-express # create connection with pods labelled app:mongo-express
  type: LoadBalancer
  ports:
  - protocol: TCP
    port: 8081 # port service is reachable at to external sources
    targetPort: 8081 # port service forwards requests to.
    nodePort: 30080 # Range is between 30000 - 326767
