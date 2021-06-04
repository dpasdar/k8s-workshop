Please use the following public image for the rest of these exercises:
`registry.gitlab.com/dpasdar/deployment-test`

1. Create deployment/service for the application image deployment-test:v1 with 3 replicas
   and access it from outside(NodePort+MiniKubeIP). Use the following bash loop afterwards 
   to continuously monitor the NodePort:
```shell
while true;do curl http://<ip address of minikube>:<node port>/;sleep 1;echo;done;
```


2. Update the version of the application to V2 while the bash loop is running on another terminal 
   and observe the results.
