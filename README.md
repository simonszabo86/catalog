start and remove container:
unsecure:
`docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db mongo`
secure:
`docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=Pass#word1 mongo`
secure docker:
`docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=Pass#word1 --network=net5tutorial mongo`

default swagger url:
`https://localhost:7005/swagger/index.html`

Database:
`MONGO_INITDB_ROOT_USERNAME=mongoadmin`

`MONGO_INITDB_ROOT_PASSWORD=Pass#word1`

Set secret password by not adding it top public config Password
`dotnet user-secrets set MongoDbSettings:Password Pass#word1`

In dev mode app end points are available on:
`http://localhost:5172`

Build a docker image (with v1 tag from the root content):
`docker build -t catalog:v1 .`

Build for docker image for hub with version v2:
`docker build -t sszabo86/catalog:v2 .`

Push built imageto docker hub:
`docker push sszabo86/catalog:v2`

Create network:
`docker network create net5tutorial`

docker run:
`docker run -it -rm -p 8080:80`

run catalog container with mongodb dependency localy and make it able to connect to catalog in net5tutorial network:
`docker run -it --rm -p 8080:80 -e MongoDbSettings:Host=mongo -e MongoDbSettings:Password=Pass#word1 --network=net5tutorial catalog:v1`

just like before but pull the image from docker hub if it is not present localy:
`docker run -it --rm -p 8080:80 -e MongoDbSettings:Host=mongo -e MongoDbSettings:Password=Pass#word1 --network=net5tutorial sszabo86/catalog:v1`

current kubernetes claster:
`kubectl config current-context`

create kubernetes secret environment variable, key is mongodb-password now:
`kubectl create secret generic catalog-secrets --from-literal=mongodb-password='Pass#word1'`

apply kubernetes catalog config:
`kubectl apply -f .\catalog.yaml`

kubernetes deployment state:
`kubectl get deployments`

kubernetes pods (a -w mutatja a változásokat):
`kubectl get pods -w`

pod logok kiíratása:
`kubectl logs {{pod neve}}`

check statefulsets:
`kubectl get statefulsets`

apply kubernetes mongodb conf:
`kubectl apply -f .\mongodb.yaml`

create more pods:
`kubectl scale deployments/catalog-deployment --replicas=3`
