AFFINITY/ANTI_AFFINITY
========================
This allows you to determine how pods are scheduled on nodes.

Node affinity allows you specify which node a pod should be scheduled on.

Pod affinity/anti-affinity allows you to determine how pods should be scheduled with respect to one another (e.g. whether two pods must always be on the same node or never on the same node).

These rules only apply during scheduling. Once pods are running, they do not take effect. Pods must be terminated an recreated for new rules to be applied.

## Node Affinity
There are two types of node affinity:
1. `requiredDuringSchedulingIgnoredDuringExecution`: this sets a hard requirement that must be met if not the pod will not be scheduled.
2. `preferredDuringSchedulingIgnoredDuringExecution`: this sets a soft requirement where the scheduler will try to meet this but if it is not met, it will schedule the pod anyway.

sample YAML
---
spec:
    affinity:
        nodeAffinity:
            requiredDuringSchedulingIgnoredDuringExecution:
                nodeSelectorTerms:
                - matchExpressions:
                    - key: env
                      operator: In
                      values:
                      - dev
            preferredDuringSchedulingIgnoredDuringExecution:
            - weight: 1
              preference:
                matchExpressions:
                - key: label-key 
                  operator: In
                  values:
                  - my-affinity #look for a node with label label-key = my-affinity
---

## Interpod Affinity/Anti-Affinity
This affinity rule applies to a specific namspace.
Similar to Node affinity, there are two types:
There are two types of node affinity:
1. `requiredDuringSchedulingIgnoredDuringExecution`
2. `preferredDuringSchedulingIgnoredDuringExecution`

SAMPLE AFFINITY.yaml
---
podAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
        - labelSelector:
            matchExpressions:
                - key: "app"
                  operator: In
                  values:
                  - affinity-app
---

SAMPLE ANTI-AFFINITY.yaml
---
podAntiAffinity:
    requiredDuringSchedulingIgnoredDuringExecution:
        - labelSelector:
            matchExpressions:
                - key: "app"
                  operator: In #Can also be NotIn, Exists, DoesNotExist
                  values:
                  - affinity-app
---
