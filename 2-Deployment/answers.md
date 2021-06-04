
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
4. Create a simple deployment of nginx with 2 replicas called deployment1

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
