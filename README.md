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