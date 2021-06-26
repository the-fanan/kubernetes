VOLUMES
============
Volumes are used to persist data in K8s. This is important for stateful pods (e.g. databases).

Storage requirements for volumes:
1. They must not depend on pod lifecycle
2. They must be accessible by all nodes
3. They must have high availability and survive even if cluster crashes.

 K8s provides an interface called Persistent Volume. This can be configured using a YAML file and is an abstract representation of your actual storage device. K8s is storage medium agnostic so configuration must be done for your particular storage medium.

pv-nfs.yaml
---
apiVersion: v1
kind: PersistentVolume
metadata:
    name: pv-name
spec:
    capacity:
        storage: 5Gi
    volumeMeta: Filesystem
    accessModes:
        - ReadWriteOnce
    persistentVolumeReclaimPolicy: Recycle
    storageClassName: slow
    mountOptions:
        - hard
        -nfsvers=4.0
    nfs:
        path: /dir/path/on/nfs/server
        server: ip-address-of-nfs-server
---
pv-google-cloud.yaml
---
apiVersion: v1
kind: PersistentVolume
metadata:
    name: pv-name
spec:
    capacity:
        storage: 5Gi
    accessModes:
        - ReadWriteOnce
    gcPersistentDisk: 
        pdName: my-disk
        fsType: ext4

Once a persistent volume is created, pods have to claim that volume. To do that, another component known as Persistent Volume Claim has to be created. 

claim.yaml
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
    name: pvc-name
spec:
    storageClassName: manual
    volumeMode: FileSystem
    accessModes:
        - ReadWriteOnce
    resources:
        requests:
            storage: 3Gi

This PVC must then be referenced in a pod definition:
pod-witch-pvc.yaml
---
apiVersion: v1
kind: Pod
metadata:
    name: pvc-pod
spec:
    containers:
        - name: pod-container
          image: a-statefull-image
          volumeMounts:
          - mountPath: "/var/www/html" (map to container in pod)
            name: pod-volume-mount
    volumes:
        - name: pod-volume-mount
          persistentVolumeClaim:
            claimName: pvc-name


Claims must be in the same namespace as pods but persistent volumees do not have to be in the same namspace as pods

Communicating between developers and cluster admins to get required pv components can be messy. So an additional component called Storage Class can be used to generate pv components on demand as needed by pvc components.

storage-class.yaml
---
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
    name: storage-class-name
provisioner: kubernetes.io/aws-ebs
parameters:
    type: io1
    iopsPerGB: "10"
    filetype: ext4

claim-from-sc.yaml
---
kind: PersistentVolumeClaim
apiVersion: v1
metadata:
    name: pvc-name
spec:
    storageClassName: manual
    volumeMode: FileSystem
    accessModes:
        - ReadWriteOnce
    resources:
        requests:
            storage: 3Gi
    storageClassName: storage-class-name

