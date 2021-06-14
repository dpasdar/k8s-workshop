1. Create a simple nginx deployment named deployment1 and access the port 80 of this deployment
   from **inside** the cluster using DNS name `myservice`.
   
**Answer**:
___   
```bash
kubectl create deployment deployment1 --image=nginx
kubectl expose deployment/deployment1 --port=80 --name=myservice
```
And then check nslookup and the port 80 inside busybox:
```shell
nslookup myservice
wget -O - myservice:80
```

