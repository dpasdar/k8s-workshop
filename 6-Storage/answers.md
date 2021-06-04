1. Create a mongodb deployment using the `mongo.yaml`, exec into the created pod
   and run the following commands to store something:

```shell
mongo
db.local.insertOne({"something": "another"})
db.local.find()
```
**Answer**:
___
```shell
kubectl create -f mongo.yaml
kubectl exec -it mongo -- sh
mongo
db.local.insertOne({"something": "another"})
db.local.find()
```
2. Remove the pod, create again using mongo.yaml and try to access that "something" again
   using the following commands:

```shell
mongo
db.local.find()
```

**Answer**:
___

```shell
kubectl delete -f mongo.yaml
kubectl create -f mongo.yaml
kubectl exec -it mongo -- sh
mongo
db.local.find()
```

3. Add necessary volume settings to make things persistent.
   Try the example above again and make sure the values are persistent even after deleting the pod.
   
**Answer**:
___
Change the mongo.yaml to the following:
```yaml
apiVersion: v1
kind: Pod
metadata:
   name: mongo
spec:
   containers:
      - image: mongo
        name: mongo
        volumeMounts:
           - mountPath: /data/db
             name: mongo-volume
   volumes:
      - name: mongo-volume
        hostPath:
           path: /tmp
```
And then try question 1 and 2 above to make sure the data is persistent.
