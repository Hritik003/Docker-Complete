# Dockerizing the backend

## dockerizng the mongoDB Service

For this we are going to official MongoDB image from the [dockerHub](https://hub.docker.com/_/mongo) and execute the command,

```
docker run --name mongoDB --rm -d -p27017:27017 mongo
```
thus exposing it to 27017 port to locally talk to our container. The MongoDB server in the image listens on the standard MongoDB port, `27017`

## Dockerizing the node-app

The mongoDB didnt require any dockerfile, but the node-app does, hence we are going to dockerize using dockerfile which we must be knowing by now,

``` dockerfile
FROM node

WORKDIR /app

COPY package.json .

RUN npm install 

COPY . .

EXPOSE 80

CMD ["node","app.js"]
```
And thus build the image `goals-backend ` .
