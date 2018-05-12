# <img src="../images/icon/docker.jpeg" style="zoom:5%" />Docker 基础命令

---

## Docker search

* 搜索image

```
$ docker search imageName
```

## Docker pull

* 获取image

```
$ docker pull imageName
```

## Docker image

* 列出所有的image文件

```
$ docker image ls
或
$ docker images
```

* 删除image文件

>imageId 可以是多个，用空格隔开

```
$ docker image rm imageId
或
$ docker rmi imageId
```

* 获取Docker Hub上的image

>官方提供的image都存放在library组里面，library是默认组，所以也可不指定library

>如果不指定tag，默认指定tag为latest

>运行image文件(如果docker发现本地没有指定运行的image文件，会自动从Docker Hub上进行抓取

```
$ docker image pull library/imageName
或
$ docker image pull library/imageName:tag
或
$ docker image pull imageName
或
$ docker image pull imageName:tag
```

```
$ docker container run imageName
```

## Docker run

* 运行image并生成容器文件

>-d 参数表示容器将以后台方式运行，并且返回容器Id

>-p 80:80参数表示容器外部端口(本机80端口)映射到容器内部80端口

>--name 参数表示给生成的容器文件命名，名称唯一

```
$ docker container run --name containerName -d -p 80:80 imageId
或
$ docker run --name containerName -d -p 80:80 imageId
```

* 容器停止时自动删除容器文件

>-d 参数表示容器将以后台方式运行，并且返回容器Id

>-p 80:80参数表示容器外部端口(本机80端口)映射到容器内部80端口

>--name 参数表示给生成的容器文件命名，名称唯一

>--rm 参数表示在容器停止运行后自动删除生成的容器文件

```
$ docker container run --name containerName -d --rm -p 80:80 imageId
或
$ docker run --name containerName -d --rm -p 80:80 imageId
```

## Docker container

* 查看运行的容器

```
$ docker ps
或
$ docker container ls
```

* 查看所有容器，包括运行和停止的

```
$ docker ps --all
或
$ docker container ls --all
```

* 停止容器

>containerId 可以是多个，用空格隔开

```
$ docker container stop containerId
或
$ docker stop containerId
```

* 强行停止容器

>containerId 可以是多个，用空格隔开

```
$ docker container kill containerId
或
$ docker kill containerId
```

* 启动容器

>containerId 可以是多个，用空格隔开

```
$ docker container start containerId
或
$ docker start containerId
```

* 删除容器

>containerId 可以是多个，用空格隔开

```
$ docker rm conainerId
或
$ docker container rm conainerId
```

## Docker exec

* 在正在运行的容器中执行命令

```
$ docker container exec [options] container command [arg...]
或
$ docker exec [options] container command [arg...]
```

>例如:进入正在运行的容器

```
$ docker container exec -it containerId /bin/bash
或
$ docker exec -it containerId /bin/bash
```

## Docker logs

* 查看日志

>-t 参数显示日志打印时间

>-f 参数以流的方式进行持续输出

```
$ docker logs -f -t containerId
或
$ docker container logs -f -t containerId
```

## Docker cp

* 从容器内拷贝文件到本机

```
$ docker container cp containerId:containerPath hostPath
或
$ docker cp containerId:containerPath hostPath
```

* 从本机拷贝文件到容器内

```
$ docker container cp hostPath containerId:containerPath
或
$ docker cp hostPath containerId:containerPath
```