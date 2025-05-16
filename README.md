sit323-737-2024-t1-prac7p
I Created my all my YAML Files So createConfigMap.yaml createHeadlessService.yaml createMongoDBSecrets.yaml createStatefulSet.yaml After that i applied all off them With Kubectl apply -f Then Kubectl get pods check if all them are running Then login to Mongo DB server kubectl exec -it Mongo-0 -- mongo Use Mongo to login in
Then rs.initiate( { _id: "rs0", members: [ { _id: 0, host : "mongo-0.mongo.default.svc.cluster.local:27017" }, { _id: 1, host : "mongo-1.mongo.default.svc.cluster.local:27017" }, { _id: 2, host : "mongo-2.mongo.default.svc.cluster.local:27017" } ] } )
Then login into other one Make one a slve Then add date db.students.insertOne({name: "sit323", age: 8}) Then go to the one off a slave to check read
Do CRUD test Do back ups
Monitoring You can use for pod in mongo-0 mongo-1 mongo-2; do echo -e "\n=== $pod ===" kubectl top pod $pod kubectl describe pod $pod kubectl logs $pod --tail=50 done
or You can use Resource usage kubectl top pods --namespace monitoring kubectl top nodes Pod health kubectl get pods -l app=mongo kubectl describe pod mongo-0 kubectl logs mongo-0 
![Uploading image.png…]()
