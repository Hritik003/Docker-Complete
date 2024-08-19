# Docker compose

Finally, this is where it gets simpler and you dont have to `docker run....` for front-end, backend...etc. Thus Docker compose gives you the flexibility to automate `multi-container ` setup.

<img width="1029" alt="image" src="https://github.com/user-attachments/assets/16161de4-cdb3-414d-89d7-184c021ef683">

## What not to expect?

- Docker Compose does **NOT replace Dockerfiles** for custom Images
- Docker Compose does **NOT replace Images** or **Containers**
- Docker Compose is **NOT suited** for managing multiple containers on different hosts (machines)

From the previous module, we built a multi-container web application for frontend, backend, and mongodb. Now we are going to do the same but using `docker-compose.yaml` file.

```yaml
    version: "3.8"
    services:
      backend:
        build: ./backend
        ports:
          - '80:80'
        volumes:
          - logs:/app/logs
          - ./backend:/app
          - /app/node_modules
        depends_on:
          - mongodb
    
      frontend:
        build: ./frontend
        ports:
          - '3000:3000'
        volumes:
          - ./frontend/src:/app/src
        stdin_open: true
        tty: true
        depends_on:
          - backend
    
      mongodb:
        image: 'mongo'
        volumes:
          - data:/data/db
    
    volumes:
      data:
      logs:




```

