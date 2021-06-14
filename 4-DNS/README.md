To observe things from inside the cluster the following temporary container/pod configuration can be used.
```shell
kubectl run -i --tty --rm debug --image=busybox:1.28 --restart=Never -- sh
```


1. Create a simple nginx deployment named deployment1 and access the port 80 of this deployment
   from **inside** the cluster using DNS name `myservice`.


