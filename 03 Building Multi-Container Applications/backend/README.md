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

But once you run the backend app, you need to make sure to change the `mongoose.connect: db link` to 

``` js
mongoose.connect(
  'mongodb://host.docker.internal:27017/course-goals',
  {
    useNewUrlParser: true,
    useUnifiedTopology: true,
  },
  (err) => {
    if (err) {
      console.error('FAILED TO CONNECT TO MONGODB');
      console.error(err);
    } else {
      console.log('CONNECTED TO MONGODB');
      app.listen(80);
    }
  }
);
```

so that now the docker knows to connect to the local mongoDB container. Also make sure to publish the port to `80` to talk to the frontend. And now executing the command succesfully works,

```
docker run --name goals-backend-app --rm -d -p80:80  goals-backend
```
