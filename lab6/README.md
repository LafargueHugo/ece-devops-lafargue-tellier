# Lab 6 

Conatiners with Docker

## Installation 

Before you can start the lab, you have to:
1. Install [Docker Desktop](https://www.docker.com/get-started) following the instructions depending on your OS.
2. Make sure your docker installation is working properly by running the following command in a terminal:
   ```
   docker run hello-world
   ```

## Run a Docker container with multiple options

1. Run the container with the following command:   
   ```
   docker run -p 12345:8080 -d hello-world-docker
   ```
   1. `-p` maps a port on your local machine to a port inside the container
   2. `-d` makes the container run in the background
2. Check if the container is running (and save the container ID) with the following command:
   ```
   docker ps
   ```
3. Open your web browser and go to `http://localhost:12345`
4. Print the logs of the container with:
   ```
   docker logs <CONTAINER_ID>
   ```
   where `CONTAINER_ID` - is the ID of the container.
3. Stop the container with:
   ```
   docker stop <CONTAINER_ID>
   ```

## Build and run a multiple container app with Docker Compose

Go to the correct folder, run : 

```bash
cd hello-world-docker-compose
```

Start the containers with `docker-compose up`
Visit `localhost:5000` in your web browser and hit refresh a couple of times
Stop the containers by running `CTRL+C` in the previous terminal
Delete the containers with:
```
docker-compose rm
```
Start the containers again 5. Start the containers with `docker-compose up`
6. Visit `localhost:5000` in your web browser and hit refresh a couple of times
7. Stop the containers by running `CTRL+C` in the previous terminal
8. Delete the containers with:
   ```
   docker-compose rm
   ```
9. Start the containers again 

## Authors

Hugo Lafargue, Rodolphe Tellier