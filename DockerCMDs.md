# Docker Commands

```shell
# Get all images
docker images
```

```shell
# Remove docker images. # -f is for force
docker rmi -f imagename;
```

```shell
# Remove containers
docker rm -f containerid
```

```shell
# list all the running containers
docker ps
docker ps -a
docker container ls
```

```shell
# List all volumns
docker volumne ls
```

```shell
# Get inside running containers
docker exec -it containername bash
```

```shell
# Run docker images in interactive way
docker run -it imagename bash
docker run imagename
docker run --name abc -it imagename
```

```shell
# Build docker base image with name different i.e. not Dockerfile
docker build -f baseimagename .
```

```shell
# Build docker images
docker build -f docker_base_image . -t rupesh123/populate_data
```

```shell
# Give name to the baseimagename while building
docker build -f baseimagename . -t newname
# e.g.: docker build -f baseimagename . -t rupesh123/dqchecks
```

```shell
# Docker build images
docker build . -t imagename
```

```shell
# Change existing image name
docker tag imagename newname:latest
```

```shell
# Login to docker
docker login
```

```shell
# Push docker image name to repo
docker push dockerhub_username/imagename
```

```shell
# Get image Name
docker pull imagename
```

```shell
# Docker logs
docker logs -f containername
```

```shell
# Docker building and running containers using docker-compose
docker-compose -f docker-compose.yml -f dev.yml up -d
# -d is for daemon
```

```shell
# Docker build image and then execute using docker-compose
docker-compose -f docker-compose.yml -f dev.yml up -d --build
```

```shell
# Down docker compose
docker-compose -f docker-compose.yml -f dev.yml down
```

```shell
# Run Individiual containers
docker-compose up -d servicename
```

```shell
# Remove all docker containers
docker rm -f $(docker ps -a -q)
```

```shell
# Remove all stopped containers
docker r
```


PID <br />
1. https://github.com/CommunityHoneyNetwork/CHN-Server/issues/17
2. https://stackoverflow.com/questions/28506722/restarting-a-docker-that-runs-supervisord-programs-keeps-pid-files-and-causes-er
