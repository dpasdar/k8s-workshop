
1. Create a simple nginx pod named pod1
   
**Answer**:
___
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod1
spec:
  containers:
  - image: nginx
    name: nginx
```
```bash
kubectl create -f blabla.yaml
```
2. Create another nginx pod called pod2

**Answer**:
___
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod2
spec:
  containers:
  - image: nginx
    name: nginx
```

Alternative:
```shell
kubectl run pod2 --image=nginx
```

3. Add a redis image into pod2

**Answer**:
___
Run
```shell
kubectl delete pod/pod2
```
Save the following file:
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod2
spec:
  containers:
  - image: redis
    name: redis
  - image: nginx
    name: nginx
```
Run
```shell
kubectl create -f blabla.yaml
```
4. Observe the IP address of pod2, then delete and recreate pod2 and observe the IP address.

**Answer**:
___
Run
```shell
kubectl get pods -o wide
```
Run
```shell
kubectl delete pods/pod2
```
Create the pod again same as above


5. Create a simple deployment of nginx with 2 replicas called deployment1

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
      - image: nginx
        name: nginx
```

6. Delete one of the pods from deployment1, wait a few seconds and see the list of pods again

**Answer**:
___
Run
```shell
kubectl get pods
kubectl delete pods/<name of the pod>
```
Wait a few seconds and then run
```shell
kubectl get pods
```
