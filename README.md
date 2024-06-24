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

Create network:
`docker network create net5tutorial`

docker run:
`docker run -it -rm -p 8080:80`

run mongodb and make it able to connect to catalog in net5tutorial network:
`docker run -it --rm -p 8080:80 -e MongoDbSettings:Host=mongo -e MongoDbSettings:Password=Pass#word1 --network=net5tutorial catalog:v1`
