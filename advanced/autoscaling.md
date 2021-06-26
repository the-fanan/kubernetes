Horizontal Pod Autoscaling
==============================
K8s can automatically scale pods horizontally based on certain metrics set.

K8s can scale based on:
1. CPU usage
2. Application based metrics like queries per second

Cluster must be started with **env** variable **ENABLE_CUSTOM_METRICS** set to `true`