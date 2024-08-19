# Dockerizing the backend

## dockerizng the mongoDB Service

For this we are going to official MongoDB image from the [dockerHub](https://hub.docker.com/_/mongo) and execute the command,

```
docker run --name mongoDB --rm -d -p27017:27017 mongo
```
thus exposing it to 27017 port to locally talk to our container. The MongoDB server in the image listens on the standard MongoDB port, `27017`
