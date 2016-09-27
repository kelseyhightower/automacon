# Manage Kubernetes TLS secrets backed by Let's Encrypt issued certificates.

## Deploy the TLS APP

```
kubectl create secret tls hightowerlabs.com --cert=certs/tls.crt --key=certs/tls.key
```

```
kubectl create -f services/tls-app.yaml
```

```
kubectl create -f deployments/tls-app.yaml
```

Visit the tls-app service endpoint and review the cert details.

In a new tab tail the `tls-app` logs:

```
kubectl logs <tls-app-pod-ip> -f
```

## Deploy the kube-cert-manager

```
kubectl create -f extensions/certificate.yaml
```

```
gcloud compute disks create kube-cert-manager --size 10GB
```

```
kubectl create -f deployments/kube-cert-manager.yaml
```

In a new tab tail the `kube-cert-manager` logs

```
kubectl logs `kube-cert-manager-pod-ip` -c kube-cert-manager -f
```

## Create the hightowerlabs.com certificate

```
cat certificates/hightowerlabs-com.yaml
```

```
kubectl create secret generic hightowerlabs --from-file=service-account.json
```

```
kubectl create -f certificates/hightowerlabs-com.yaml
```


