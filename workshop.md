# InfluxDB

Install influxdb client

https://docs.influxdata.com/influxdb/v1.2/introduction/installation

```
helm install stable/influxdb --name influxdb \
  --set service.type=NodePort
```

```
INFLUX_HOST=$(minikube service influxdb-influxdb --format "{{.IP}}")
```

```
INFLUX_PORT=$(minikube service influxdb-influxdb --format "{{.Port}}")
```

```
influx --host ${INFLUX_HOST} --port ${INFLUX_PORT}
```

```
show databases
```

```
use telegraf
```

```
SHOW MEASUREMENTS
```


Find the container consuming the most memory:

```
select pod_name,max(memory_usage_bytes) from kubernetes_pod_container
```

## Telegraf

KUBERNETES_HOST=$(minikube ip)

```
helm install --name telegraf \
  --set daemonset.config.outputs.influxdb.urls={http://influxdb-influxdb:8086} \
  --set daemonset.config.inputs.kubernetes.url=http://${KUBERNETES_HOST}:10255 \
  stable/telegraf
```

## Chronograf

```
helm install stable/chronograf --name chronograf \
  --set service.type=NodePort
```

```
minikube service chronograf-chronograf
```

Connection String:

```
http://influxdb-influxdb:8086
```

Name:

```
minikube
```

## Kapacitor

```
https://docs.influxdata.com/kapacitor/v1.2/
```

```
helm install stable/kapacitor --name kapacitor \
  --set service.type=NodePort \
  --set influxURL=http://influxdb-influxdb:8086
```

```
- name: "KAPACITOR_KUBERNETES_ENABLED"
        value: "true"
- name: "KAPACITOR_KUBERNETES_IN_CLUSTER"
        value: "true"
```

```
export KAPACITOR_URL=$(minikube service kapacitor-kapacitor --url)
```

```
kapacitor stats general
```
