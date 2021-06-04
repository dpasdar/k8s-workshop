1. Create a simple nginx pod named pod1 and access the port 80 of this pod
   from **inside** the cluster

**Answer**:
___
```bash
kubectl run pod1 --image=nginx
kubectl expose pod/pod1 --port=80
```
And then check the port 80 inside busybox:
```shell
wget -O - <ip address of the service>:80
```

2. Create a deployment from image `ealen/echo-server` with 2 replicas, expose it
   with a service and access it from **outside**.

**Answer**:
___
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: deployment1
spec:
  replicas: 2
  selector:
    matchLabels:
      app: deployment1
  template:
    metadata:
      labels:
        app: deployment1
    spec:
      containers:
      - image: ealen/echo-server
        name: echo
```
   a. Create a service:
```shell
kubectl expose deployment/deployment1 --type=NodePort --port=80
```
   b. Find the external IP of minikube:
```shell
minikube ip
```
   c. Find the port number of the created NodePort service:
```shell
kubectl get services
```
   d. Check that port from your local machine:
```shell
wget -O - <ip address of minikube>:<port number of the NodePort service>
```
