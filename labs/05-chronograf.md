# Chronograf

## What is Chronograf?

[Introduction to Chronograf](https://docs.influxdata.com/chronograf/v1.3)

## Install Chronograf

```
helm install stable/chronograf --name chronograf \
  --set service.type=NodePort
```

Verify that chronograf is running:

```
kubectl get pods
```

## Visit the Chronograf Dashboard

Use minikube to connect to the Chronograf service:

```
minikube service chronograf-chronograf
```

Configure the InfluxDB connection details:

```
Connection String: http://influxdb-influxdb:8086
Name: minikube
```

Click the "Add Source" button. At this point you can explore the Chronograf dashboard.
