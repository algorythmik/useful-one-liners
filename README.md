# useful-one-liners

## screen 
- Start a named session `screen -S name`
- list of screens:
`screen -ls`
- re-attacn to a screen:
`screen -r session-name`
- kill a screen: 
`ctrl` + `a` and then `k`
 

## Docker
- Build and Run:
```
docker build -t my_docker .
docker run -p 9000:9000 my_docker
```
- Connecting to the container and geting a shell:
`docker container run -it`: start the container interactively (i for interactive and t for pseudo tty)

`docker container exec -it`: run additional command in existing container

`docker exec -it <mycontainer> /bin/bash`

- Delete all containers in docker:

`docker rm $(docker ps -a -q)`

- some useful arguments:
    - `--name` to name a container
    - `--detach` run in the detached mode
    - `--env` (`-e`) pass in an environment variable
`docker container stop [list of names]` to stop containers

- Inspecting containers:

`docker container top CONTAINER`: list all running processes of a container

`docker container inspect`: displaying details of one  or more container

`docker container stats`: displays perfromance stats for all containers in a real-time stream

## Kuberneters
- Get list of pods:

`kubectl -n namespace get pods`
- To see more details

`kubectl describe po/name`

- To see the logs:
`kubectl logs po/podname`

- To see the running logs:

`kubectl logs -f po/podname`

- Connecting to the pod

`kubectl exec -it pod-id /bin/bash`

- After connecting the pod, You can do port-forwarding to see the tensor board:
Open another tab and run tensorboard:

`Tensor board —logdir=path_to_logdir`

and then portforward:

`kubectl port-forward pod-id 6006:6006`

- Copy to and from a pod:
    - Copy /tmp/foo local file to /tmp/bar in a remote pod in namespace

`kubectl cp /tmp/foo <some-namespace>/<some-pod>:/tmp/bar`

- Copy /tmp/foo from a remote pod to /tmp/bar locally:

`kubectl cp <some-namespace>/<some-pod>:/tmp/foo /tmp/bar`

## s3
sync  an s3 bucket where only keys mathig specific patterns are included:
```
aws s3 sync --sse aws:kms --sse-kms-key-id keyid s3://s3bukcet/keys/ mylocalpath --exclude '*' --include *.csv' --include '*.tiff'
```
