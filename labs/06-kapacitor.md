# Kapacitor

## What is Kapacitor?

[Introduction to Kapacitor](https://docs.influxdata.com/kapacitor/v1.2)

## Install Kapacitor

```
helm install stable/kapacitor --name kapacitor \
  --set service.type=NodePort \
  --set influxURL=http://influxdb-influxdb:8086
```

Verify kapacitor is running:

```
kubectl get pods
```

## Enable Kubernetes Integration

Edit the kapacitor deployment:

```
kubectl edit deployment kapacitor-kapacitor
```

Add the following env vars:

```
- name: "KAPACITOR_KUBERNETES_ENABLED"
  value: "true"
- name: "KAPACITOR_KUBERNETES_IN_CLUSTER"
  value: "true"
```

## Verify The Kapacitor Installation

```
export KAPACITOR_URL=$(minikube service kapacitor-kapacitor --url)
```

```
kapacitor stats general
```
