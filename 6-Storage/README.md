1. Create a mongodb deployment using the `mongo.yaml`, exec into the created pod 
   and run the following commands to store something:
   
```shell
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
3. Add necessary volume settings to make things persistent. 
   Try the example above again and make sure the values are persistent even after deleting the pod.
