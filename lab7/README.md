# Lab 7

Container orchestration with Kubernetes

## Installation 

[Install Minikube](https://kubernetes.io/docs/tasks/tools/install-minikube/) following the instructions depending on your OS.

Start Minikube with:
```
minikube start
```

Verify that everything is OK with:
```
minikube status
```
## Testing 

run : 
```bash
kubectl apply -f deployment.yaml
```

Then go to your http://localhost:8080 and refresh the page cpuple of times. 

## Authors

Hugo Lafargue, Rodolphe Tellier