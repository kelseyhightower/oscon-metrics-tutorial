# Autoscaling with Kapacitor

In this lab you will follow the [Kapacitor + Kubernetes Autoscaling](https://github.com/influxdata/k8s-kapacitor-autoscale) tutorial on your local Kubernetes clusters.

## Deploy the Example Application

Create the `app` replicaset:

```
kubectl create -f https://raw.githubusercontent.com/kelseyhightower/oscon-metrics-tutorial/master/replicasets/app.yaml
```

Create the `app` service

```
kubectl create -f https://raw.githubusercontent.com/kelseyhightower/oscon-metrics-tutorial/master/services/app.yaml
```

## Define and Enable the Autoscale Task

```
kapacitor define autoscale -tick autoscale.tick -type stream -dbrp autoscale.autogen
```

```
kapacitor enable autoscale
```

```
kapacitor show autoscale
```

```
watch kubectl get pods
```

### Load test the Example Application

```
export APP_URL=$(minikube service app --url)
```

```
while true; do curl $APP_URL; done
```
