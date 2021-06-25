HELM
=======
This is a package manager for K8s. It contains YAML files already packaged and configured to help you ease setting up your applications. The bundles of YAML files are called **Helm Charts**.

SAMPLE HELM TEMPLATE FILE
pod.yaml
---
apiVersion: v1
kind: Pod
metadata:
    name: {{ .Values.name }}
spec:
    containers:
    -   name: {{ .Values.container.name }}
        image: {{ .Values.container.image }}
        port: {{ .Values.container.port }}

---
SAMPLE VALUES FILE
values.yaml
---
name: pod-1-values
container:
    name: pod-1-container
    image: pod-1-image
    port: 9000

---
Folder structure for Helm chart packaging

mychart/
    Chart.yaml (meta data on cahrt)
    values.yaml (default values you can override)
    charts/ (charts your template is dependent on)
    template/ (your main template)

---
Command to install chart with values
`helm install --values=FILE_NAME_OF_VALUES.yaml CHART_NAME`



