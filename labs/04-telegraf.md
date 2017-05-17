# Telegraf


## What is Telegraf?

[Introduction to Telegraf](https://docs.influxdata.com/telegraf/v1.3)

## Install Telegraf

Set the minikube cluster IP address:

```
KUBERNETES_HOST=$(minikube ip)
```

Install telegraf using helm:

```
helm install --name telegraf \
  --set daemonset.config.outputs.influxdb.urls={http://influxdb-influxdb:8086} \
  --set daemonset.config.inputs.kubernetes.url=http://${KUBERNETES_HOST}:10255 \
  stable/telegraf
```

Verify telegraf is running:

```
kubectl get pods
```

## Exploring Telegraf Metrics

Connect to the influxDB server:

```
influx --host ${INFLUX_HOST} --port ${INFLUX_PORT}
```

List the databases:

```
show databases
```

Use the `telegraf` database:

```
use telegraf
```

List the available measurements:

```
SHOW MEASUREMENTS
```

Find the container consuming the most memory:

```
select pod_name,max(memory_usage_bytes) from kubernetes_pod_container
```

Exit the influx interactive prompt:

```
exit
```
