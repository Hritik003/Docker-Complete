# Dockerizing frontend

Lets learn how we are going to dockerize this?

## Dockerizing the React-app

Alright, now since we are done dockerizing the backend and mongoDB, its time to dockerize the last container, i.e  `react-app`.  Lets do this by again creating the dockerfile,

```dockerfile
FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD ["npm","start"]
```

and thus build the image  `goals-frontend`.

