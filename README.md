# Automacon: Kubernetes for Sysadmins - Guided Tutorial

## Create a Kubernetes Cluster

```
gcloud container clusters create k0 --num-nodes 8
```

## Start the kubeclt proxy

The labs in this tutorial require the `kubectl proxy` to be running. In a new tab start the `kubectl proxy`

```
kubectl proxy
```

## Labs

* [Custom Scheduler](docs/scheduler.md)
