# Docker Networks

## List Existing Docker Networks

```shell
docker network ls
```

## Create a new Docker Network

```shell
docker network create -d bridge servBridge

# -d (Driver)
# bridge (The driver)
# servBridge (The network name)
```
