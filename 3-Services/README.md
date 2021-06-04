To observe things from inside the cluster the following temporary container/pod configuration can be used.
```shell
kubectl run -i --tty --rm debug --image=busybox --restart=Never -- sh
```


1. Create a simple nginx pod named pod1 and access the port 80 of this pod 
   from **inside** the cluster.

2. Create a deployment from image `ealen/echo-server` with 2 replicas, expose it 
   with a service and access it from **outside**
