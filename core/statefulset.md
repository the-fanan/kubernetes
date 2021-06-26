STATEFULL SET
=================
This is a component for deploying stateful applications (e.g. databases). It is like a deployment but for stateful applications. It gives pods a sticky identity as stateful pods are not interchangeable.

In stateful applications, one pod only is allowed to write and this is called the master pod while many other pods are allowed to read and are called slave pods.

The pods also do not share the same volumes and hence have to consistenly synschronize data.

