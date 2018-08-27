# useful-one-liners

Some useful one-liners that I use in daily works:
## Docker
Build and Run:
```
docker build -t my_docker .
docker run -p 9000:9000 my_docker
```
Connecting to the containder and getting a bash:

`docker exec -it <mycontainer> /bin/bash`

Delete all containers in docker:

`docker rm $(docker ps -a -q)`

