RESOURCE USAGE MONITORING
==========================
It is important to monitor your cluster to ensure enough resources are available and everything runs smoothly. To monitor your cluster, we use tool called **Heapster**. It allows you to view clutster metrics via REST endpoints. Heapster needs a data store to store metric information. You can use InfluxDB, Apache Kafka, Google Cloud Monitoring and other storages.

[Heapster YAML Repo](https://github.com/kubernetes/heapster/tree/master/deploy/kube-config/influxdb)

From K8s 1.11+ Heapster will be deprecated for metrics-server.
[Metric Server YAML](https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml)

Metric server is in the **kube-system** namespace so to view it, run command `kubectl get pods -n kube-system`

Once metrics server is installed, you can run:
`kubectl top node` to get node metrics
`kubectl top pod` to get pod metrics etc.

[Troubleshoot Issues with Metric Server](https://www.linuxsysadmins.com/service-unavailable-kubernetes-metrics/)