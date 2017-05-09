# Minikube

In this lab you will make sure that [minikube](https://github.com/kubernetes/minikube) is installed and running.

## Verify the Minikube Installation

Ensure minikube is running:

```
minikube status
```

```
minikubeVM: Running
localkube: Running
```

Verify kubectl is set to the minikube context:

```
kubectl config current-context
```
```
minikube
```

Verify the kubectl version:

```
kubectl version
```

```
Client Version: version.Info{Major:"1", Minor:"6", GitVersion:"v1.6.2", GitCommit:"477efc3cbe6a7effca06bd1452fa356e2201e1ee", GitTreeState:"clean", BuildDate:"2017-04-19T20:33:11Z", GoVersion:"go1.7.5", Compiler:"gc", Platform:"darwin/amd64"}
Server Version: version.Info{Major:"1", Minor:"6", GitVersion:"v1.6.0", GitCommit:"fff5156092b56e6bd60fff75aad4dc9de6b6ef37", GitTreeState:"dirty", BuildDate:"2017-04-07T20:46:46Z", GoVersion:"go1.7.3", Compiler:"gc", Platform:"linux/amd64"}
```


