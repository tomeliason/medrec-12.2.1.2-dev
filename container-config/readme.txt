execute the medrec.sql file to create the medrec user and tables and load data.

modify the oradatasource.properties to match your db instance - connection string, etc.

place the oradatasource.properties file somewhere on the file system, and one example to run the docker container is:

docker run --name medrec -p 7011:7011 -v /root/src/container-config:/container-config oradb-medrec:12.2.1.2-dev

browse to localhost:7001/medrec - login as administrator/administrator123 - if that's successful your WLS app is connected to the DB


for k8s, create a configmap that loads in your oradatasource.properties:
kubectl create configmap medrec-container-config-dev --from-file=oradatasource.properties

start the container in the cluster:
kubectl apply -f medrec.yaml
