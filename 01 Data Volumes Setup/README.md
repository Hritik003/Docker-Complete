# Volumes, Bind Mount and its setup


This repo is mainly about the usage of volumes in the containers, and my notes on how does data is persistent inside the volumes even when container is removed.

## Important Notes on Volumes:

- Anonymous volumes are only deleted whenever container shuts down.
- Named volumes in the other case, is persistent even though the container is removed.

  usage of named volumes example:

  ```
  docker run -d -p3000:80 --rm --name <container_name> -v <volume_name>:/app/feedback <image_name>:<tag>
  ```

  ![image](https://github.com/user-attachments/assets/e6f20120-debf-401e-87ab-41a79bb47575)


## Volumes-Bind Mount Summary

- ### Anonymous Volume:
  With anonymous volumes, you create a volume which is kind of attached to a container. It's removed if the container is removed. It survives container shut down and restart, but if it's removed, it's gone and thereforeif you use the dash dash rm when you ran the container, of course the volume is all gone when you stop the container because stopping then basically also means removing the container. Therefore, since it is removed when the container is removed, you can't use anonymous volumes to share data across containers. And you also can't use it to save data across container destruction and recreation as you saw.
```
docker run -v /app/data...
```
- ### Named Volume
  Named volumes are volumes which you create manually but with a name. They are created in `/var/lib/docker/volumes` and can be referenced to by only their **name**. Let's say you create a volume called "mysql_data", you can just reference to it like this `docker run -v mysql_data:/containerdir IMAGE_NAME`
```
docker run -v data:/app/data...
```
- ### Bind Mount
  Bind mounts are basically just binding a certain directory or file from the host inside the container. We use Bind Mounts in our code to reflect subsequent changes in the code in the running container **instantly**.
```
docker run -v /path/to/code:/app/data...
```

## What should I use?

What you want to use comes mostly down to either preference or your management. If you want to keep everything in the "docker area" (`/var/lib/docker`) you can use **volumes**. If you want to keep your own directory-structure, you can use **binds**.



  
