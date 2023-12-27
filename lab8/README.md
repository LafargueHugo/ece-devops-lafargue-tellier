# Lab 8 

## Installation

1. Install [Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) following the instructions depending on your OS.

## Usage

Start Minikube with:

```
minikube start
```

3. Verify that everything is OK with:

```
minikube status
```
go to [`lab8/emptyDir`](lab8/emptyDir).

## 1. Use `emptyDir` storage

Run a pod applying configuration:

```
kubectl apply -f lab/emptyDir/deployment.yml
```

Enter to a container and `curl` localhost

List all the pods and find a name of a created pod

```
kubectl get pods
```

Enter to the container:

```
kubectl exec -it <POD_NAME> bash
```

Run `curl localhost` (or `curl localhost/index.html`, because by default of Nginx will point to `index.html` if you do not specify the filename)

it will output:

```
Hello from Kubernetes storage!
```


## 2. Use `hostPath` storage

go to [`lab8/HostPath`](lab8/HostPath).

Run a pod applying configuration:

```
kubectl apply -f lab/hostPath/deployment.yml
```

Ensure that `curl localhost` responds with 403 error (step 3 in the previous task).

Enter the VM with `minikube ssh` command.

Run `curl localhost` from the container (not from the VM). It will output:

```
Hello from Kubernetes storage!
```

## Authors

Hugo Lafargue, Rodolphe Tellier