# InfluxDB

In this tutorial you will install the influxdb CLI tool and deploy the influxDB into your local Kubernetes cluster using Helm.

## What is InfluxDB

[Introduction to InfluxDB](https://docs.influxdata.com/influxdb/v1.2)

## Deploy InfluxDB

In this section you will deploy a InfluxDB server into your Kubernetes cluster.

```
helm install stable/influxdb --name influxdb \
  --set service.type=NodePort
```

## Install the influx client

In this section you will download and test the influxdb CLI client.

[https://docs.influxdata.com/influxdb/v1.2/introduction/installation](https://docs.influxdata.com/influxdb/v1.2/introduction/installation)

Set the InfluxDB server host and port:

```
INFLUX_HOST=$(minikube service influxdb-influxdb --format "{{.IP}}")
```

```
INFLUX_PORT=$(minikube service influxdb-influxdb --format "{{.Port}}")
```

Connect to the InfluxDB server:

```
influx --host ${INFLUX_HOST} --port ${INFLUX_PORT}
```

List the available databases:

```
show databases
```

Exit the influx interactive prompt:

```
exit
```
