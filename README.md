# go-docker-compose

## introduction

This is a demo project for test graceful shutdown function

by docker-compose 

## how to run
```script===
    docker-compose up -d 
```
## scale up container

```script===
    docker-compose up -d  --scale app=2
```
## do test by curl

```script===
curl -v -H Host:app.docker.localhost http://127.0.0.1:8088
```

## orginal docker-compose up will recreate original container when scale 

but with --no-recreate

this would just create not existed container only

```script===
docker-compose up -d --scale app=3 --no-recreate
```
## kill last two container
```script===
docker stop -t 30 \
>   $(docker ps --format "table {{.ID}}  {{.Names}}  {{.CreatedAt}}" | \
>   grep app | \
>   sort -k2 | \
>   awk -F  "  " '{print $1}' | head -2)
```
## remove no used image
```script===
docker container prune -f
```
## reference document
[graceful shutdown use docker-compose with rolling update](https://blog.wu-boy.com/2020/02/graceful-shutdown-using-docker-compose-with-rolling-update/)