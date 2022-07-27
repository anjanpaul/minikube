# minikube start
minikube is local Kubernetes, focusing on making it easy to learn and develop for Kubernetes.

All you need is Docker (or similarly compatible) container or a Virtual Machine environment, and Kubernetes is a single command away: minikube start

## What you’ll need

* 2 CPUs or more
* 2GB of free memory
* 20GB of free disk space
* Internet connection
* Container or virtual machine manager, such as: Docker, Hyperkit, Hyper-V, KVM, Parallels, Podman, VirtualBox, or VMware Fusion/Workstation


To install the latest minikube stable release on x86-64 macOS using binary download:

```
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64
sudo install minikube-darwin-amd64 /usr/local/bin/minikube

```

Start your cluster:

```
minikube start --nodes 2 -p local-cluster --driver=docker                                                                                     at 03:41:22 AM

```

## Interact with your cluster

If you already have kubectl installed, you can now use it to access your shiny new cluster:

```
kubectl get po -A

```

Alternatively, minikube can download the appropriate version of kubectl and you should be able to use it like this:

```
minikube kubectl -- get po -A

```

# Argo CD

## Requirements
* nstalled kubectl command-line tool.
* Have a kubeconfig file (default location is ~/.kube/config).
* CoreDNS. Can be enabled for microk8s by microk8s enable dns && microk8s stop && microk8s start

## 1. Install Argo CD

```
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

```

## 2.Port Forwarding
Kubectl port-forwarding can also be used to connect to the API server without exposing the service.

```
kubectl port-forward svc/argocd-server -n argocd 8080:443

```

To get admin password:

```
kubectl get secret argocd-initial-admin-secret -n argocd -o yaml

```

To decode secrets:
```
echo OTBFLXRUWTRBWC1SYXdDRA== | base64 --decode

```

The output you will get a password

AND BOOM
