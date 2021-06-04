Please use the following public image for the rest of these exercises:
`registry.gitlab.com/dpasdar/deployment-test`

1. Create deployment/service for the application image `deployment-test:v1` with 3 replicas
   and access it from outside(NodePort+MiniKubeIP). Use the following bash loop afterwards
   to continuously monitor the NodePort:
```shell
while true;do curl http://<ip address of minikube>:<node port>/;sleep 1;echo;done;
```

**Answer**:
___
```shell
kubectl create deployment test1 --image=registry.gitlab.com/dpasdar/deployment-test:v1 --replicas=3
kubectl expose deployment/test1 --type=NodePort --port=80 --name=test1service
kubectl get services/test1service
minikube ip
```

2. Update the version of the application to `deployment-test:v2` while the bash loop is running on another terminal
   and observe the results.
   
**Answer**:
___
```shell
kubectl edit deployment/test1
```
and change the image name accordingly (:v2), after saving the file the loop should show some
requests going to the old version, and some to the new version until the services converge.
