1. Find all the nodes?
   
**Answer**:
___
```shell
kubectl get nodes
```

2. Find all the pods (in default namespace)?

**Answer**:
___
```bash
kubectl get pods
```
3. Find all the important pods/pods with the note label set to important 

**Answer**:
___
```bash
kubectl get pods -l note==important
```
4. Find all the services

**Answer**:
___
```bash
kubectl get services
```
5. Find the IP/Address of pod1

**Answer**:
___
```bash
kubectl get pods -o wide
```
```shell
kubectl get pods/pod1 -o wide
```
```shell
kubectl describe pods/pod1 | grep IP
```
6. Find the name of all the container images for pod2

**Answer**:
___
```bash
kubectl get pods/pod2 -o yaml
```
7. How many pods are there in kube-system namespace?

**Answer**:
___
```bash
kubectl get pods --namespace kube-system
```
7 pods.
