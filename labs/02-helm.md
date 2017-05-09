# Helm

In this lab you will install [helm](https://github.com/kubernetes/helm) on your local machine.

## What is Helm?

[Introduction to Helm](https://github.com/kubernetes/helm#kubernetes-helm)

## Install Helm

Install helm using the [installation docs](https://github.com/kubernetes/helm#install)

## Initialize Helm and install Tiller

```
helm init
```

```
helm repo update
```

Install a sample chart:

```
helm install --name oscon-mysql stable/mysql
```

List installed charts:

```
helm ls
```

Delete the mysql deployment

```
helm delete oscon-mysql
```
