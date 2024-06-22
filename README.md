start and remove container:

`docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db mongo`

`docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=Pass#word1 mongo`

default swagger url:

`https://localhost:7005/swagger/index.html`

Database:

`MONGO_INITDB_ROOT_USERNAME=mongoadmin`

`MONGO_INITDB_ROOT_PASSWORD=Pass#word1`

Set secret password by not adding it top public config Password

`dotnet user-secrets set MongoDbSettings:Password Pass#word1`
