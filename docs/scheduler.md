# Lab: Custom Scheduler

## Download Binaries

Download the `scheduler` and `annotator` binaries:

### OSX

```
wget https://storage.googleapis.com/automacon/darwin/annotator
```

```
wget https://storage.googleapis.com/automacon/darwin/scheduler
```

```
chmod +x annotator scheduler
```

### Linux

```
wget https://storage.googleapis.com/automacon/linux/annotator
```

```
wget https://storage.googleapis.com/automacon/linux/scheduler
```

```
chmod +x annotator scheduler
```

## Annotate The Worker Nodes

```
./annotator
```

At any time you can rerun the annotator with the `-l` flag to list the current annotations:

```
./annotator -l
```

## Create a Deployment

```
cat deployments/nginx.yaml
```

```
kubectl create -f deployments/nginx.yaml
```

```
kubectl get pods
```

## Run the Scheduler

```
./annotator -l
```

```
./scheduler
```

```
kubectl get pods -o wide
```

## Deploy the Scheduler

```
kubectl create -f deployments/scheduler.yaml 
```

## Scale the Deployment

In a new tab tail the scheduler logs

```
kubectl get pods -l app=scheduler
```

```
kubectl logs <scheduler-pod-id> -c scheduler -f
```

```
kubectl scale deployments nginx --replicas=10
```
