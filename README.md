# Using a dedicated dev Dockerfile and a Multi-Step Dockerfile

This simple ReactJs application is used for the Udemy course by Stephen Grider:

[Docker and Kubernetes: The Complete Guide](https://www.udemy.com/course/docker-and-kubernetes-the-complete-guide/)

## Dockerfile.dev and docker-compose.yml

The *docker-compose.yml* is using the *Dockerfile.dev* file.
Running ...

    docker compose up -d

... will
* use the *Dockerfile.dev* entrypoint of *npm run start* which start the Application in dev mode
* expose the React.js application on port *3333*
* and mount the working directory as a volume into the container, so code changes in your file system will be reflected within the container

FYI:

In the *docker-compose.yaml*, under *volumes* you see this line:

    - /app/node_modules

As you can see here we don't see a ":".
This means that no volume from the host system (your dev machine) is mounted here into the container.
Instead this line makes sure that the existing *node_modules* directory within the container is **not** overwritten.

## Dockerfile

  docker compose up -d --build

## Stop the application via do

cker compose

    docker compose down