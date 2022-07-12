# Commands
```
d kill $(d ps -q)
docker images | grep {keywords}} |awk '{print $3}'
docker rm $(docker ps -a -q)
docker rmi $(docker images -q)
docker container prune
docker image prune
docker inspect {container}
```
---
# Dockerfile
[Best practices for writing Dockerfiles](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
- Create ephemeral containers
- Understand build context
- Exclude with .dockerignore

---
# Alpine image

## Clear cache to reduce image size

```
RUN apk update

#...add packages

RUN rm -rf /var/cache/apk/*
```

Or

```
RUN apk add --no-cache package
```
### references
[docker - Alpine Dockerfile Advantages of --no-cache Vs. rm /var/cache/apk/* - Stack Overflow](https://stackoverflow.com/questions/49118579/alpine-dockerfile-advantages-of-no-cache-vs-rm-var-cache-apk)


## alpine repositories and php version
- 3.5 with php7.0.33
- 3.7 with php7.1.
- 3.9 with php7.2.14

---

# Connect to the localhost from inside a docker container

just connect to your mysql service using the host `host.docker.internal` (instead of the 127.0.0.1 in your connection string).

[reference](https://docs.docker.com/desktop/networking/#i-want-to-connect-from-a-container-to-a-service-on-the-host)


# Copy file to local

`docker container cp mynginx:/etc/nginx .`
上面命令的含义是，把mynginx容器的_etc_nginx拷贝到当前目录。不要漏
掉最后那个点。

# Build dockerfile
```
docker run [-v $(pwd):/app] [--rm] {image[:tag]}
docker build -t debug . --network=host --no-cache

```

```
{command}}
RUN apk add -t .build-deps $PHPIZE_DEPS \\
 && pecl install xdebug-2.6.0 \\
 && docker-php-ext-enable xdebug
RUN apk del .build-deps

```
