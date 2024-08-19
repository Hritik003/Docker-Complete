# Working with Multi-container app

Till now, we have learnt everything about dockerizing the application and networking between the containers. In this demo project we are going to practice all in one application, yes that is correct! We are going to build three building blocks(aka containers) and sign specific boundaries for each container,

<img width="1075" alt="image" src="https://github.com/user-attachments/assets/5e05c401-7ade-42ae-84d2-27dbcf4ca18c">

---

## Repo contains?

The neccessary docker files for each folder has been created inside the repo,
- backend
- frontend

## Dockerizing in a network

After dockerizing the respective backend,frontend lets try to dockerize in the same network so that we dont have to publish any ports in the backend, nevertheless lets publish the 3000 port in the frontend as it is for now,
and the network name be  `goals-net`.

> **_NOTE:_**  Make sure to change the `http://localhost....` to `http://<backend-container-name>....` in my case `http://goals-backend-app....`. in the app.js file of the frontend to talk to the backend in the same network.

```
docker create network goals-net
```

- Dockerizing the mongodb in the `goals-net` network:
  ```
  docker run  --network goals-net --name mongodb --rm -d mongo
  ```
- Dockerizing the node-app in the `goals-net` network:
  ```
  docker run --rm -d --network goals-net --name goals-backend-app goals-backend
  ```
- Dockerizing the react-app in the `goals-net` network:
  ```
  docker run --rm -d --network goals-net --name goals-frontend-app -p3000:3000 goals-frontend
  ```

After successfully running the three containers, the `localhost:3000` in the browser pops with this error, hm..now what is this?

![image](https://github.com/user-attachments/assets/53ecc32f-9595-44a3-9984-b7a810a3d6a7)

