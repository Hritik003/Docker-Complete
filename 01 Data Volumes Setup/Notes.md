# Volumes and its setup


This repo is mainly about the usage of volumes in the containers, practicing how does data is persistent inside the volumes even when container is removed.

## Important Notes on Volumes:

- Anonymous volumes are only deleted whenever container shuts down.
- Named volumes in the other case, is persistent even though the container is removed.

  usage of named volumes example:

  ```
  docker run -d -p3000:80 --rm --name <container_name> -v <volume_name>:/app/feedback <image_name>:<tag>
  ```

  
