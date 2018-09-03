# useful-one-liners

Some useful one-liners that I use in daily works:
## Docker
- Build and Run:
```
docker build -t my_docker .
docker run -p 9000:9000 my_docker
```
- Connecting to the container and getting a bash:

`docker exec -it <mycontainer> /bin/bash`

- Delete all containers in docker:

`docker rm $(docker ps -a -q)`

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
