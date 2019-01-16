Show all running containers:

```
docker ps
```

Kill all running containers:

```
docker kill $(docker ps -q)
```

Building a Docker image from a current directory:

```
docker build -t [image name] .
```

Running the container and exposing container port 5000 to localhost:5000:

```
docker run -p 5000:5000 [image name]
```

Running the container with custom hosts entry:

```
docker run --add-host=domain:ip [image name]
```

Building an image and running with a custom host available:

```
docker build -t [image name] . && docker run -p 5000:5000 --add-host=[domain]:[ip] [image name]
```

Eg. 

```
docker build -t my-api . && docker run -p 5000:5000 --add-host=consul:10.208.67.163 my-api
```

Jump into the Docker container Bash:

```
docker ps # copy the container ID you want to jump into
sudo docker exec -it [container id] /bin/bash
```
