NAMESPACES
=============
Namespaces allow you to organize and group your resources. This way, you can run and manage multiple custers within your single cluster.
Kubenetes comes with four default namespaces:
1. **Kube System**: Contains system processes (Master and Kubectl). !!DO NOT MODIFY ANYTHING IN THIS NAMESPACE!!
2. **Kube Public**: Contains publicly accessible data. This is cluster information that can be accessed without authentication via `kubectl cluster-info`
3. **Kube Node Lease**: Contains info about the health and availability of nodes
4. **Default**: This is the configurable namespace automatically created for you to run a cluster.


To create a namespace run `kubectl create namespace NAME-OF-NAME-SPACE`
You can also specify namespace in the component metadata of your configuration files.

Why Namespaces?
Grouping resources allow for separation of concerns and hence makes it easy to manage your resources. E.g. You can group namespaces based on service type (databases vs applications) or based on application type itself (e.g. frontend vs APIs).
This allows for your team to easily manage a particular namespace tailored to the feature, or service they are working on.

It is recommended that is your project is relatively small and you do not have up to 10 users, you do not need to namespace your clusters.

Things To Note About Namespaces
=================================
1. You cannot share ConfigMap or Secret.
2. You can share Services. Done so by doing SERVICE_NAME.SERVICE_NAMESPACE.
3. You cannot namespace Volumes and Nodes.
4. `kubectl api-resources --namespaced=false` gives you resources not bound to a namespace
5. `kubectl api-resources --namespaced=true` gives you resources bound to a namespace
6. To specify namespace to run kubectl command append the `-n` flag like so `kubectl get pods -n NAMESPACE` OR `kubectl apply -f PATH_TO_CONFIG --namespace=NAMESPACE`