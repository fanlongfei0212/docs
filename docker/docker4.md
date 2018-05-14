# <img src="../images/icon/docker.jpeg" style="zoom:5%" />Docker Volumes

---

** 
Docker作为与外部环境所隔离的容器，而且一旦数据容器被销毁或者基于某种原因修改了镜像，需要生成并使用新容器的时候，
如何保存之前的数据就成了一个很大的问题。为了解决这种问题，在Docker中可以将本机的目录作为「挂载卷」，容器与本机
的数据是共享的，无论是本机数据发生变化，还是容器数据发生变化，共享的数据都会保持一致并且会同时存储在容器的内部和
本机作为「挂载卷」的指定目录。而且，在Docker中，除了可以指定目录为「挂载卷」，还可以将容器作为数据容器，以「挂载卷」
的方式挂载到其他容器上，既能保存容器内部数据，还可以做到多容器之间的「数据共享」。
**

## 挂载卷为目录

* 不指定本机具体目录为挂载卷

>不指定本机具体目录作为挂载卷，docker会在宿主机生成一个地址目录

>如果指定的容器内部地址不存在则容器会进行自动创建

``` bash
$ docker run --name containerName -d -p hostPort:containerPort -v containerPath imageId
或
$ docker container run --name containerName -d -p hostPort:containerPort -v containerPath imageId
```

>查看docker生成在宿主机的挂载卷地址，容器信息里Mounts中Source就是宿主机上挂载卷的地址

``` bash
$ docker inspect containerid 
```

* 挂载卷为当前目录

>如果指定的容器内部地址不存在则容器会进行自动创建

``` bash
$ docker run --name containerName -d -p hostPort:containerPort -v $PWD:containerPath imageId
或
$ docker container run --name containerName -d -p hostPort:containerPort -v $PWD:containerPath imageId
```

* 指定本机具体目录为挂载卷

>如果指定的容器内部地址不存在则容器会进行自动创建

``` bash
$ docker run --name containerName -d -p hostPort:containerPort -v hostPath:containerPath imageId
或
$ docker container run --name containerName -d -p hostPort:containerPort -v hostPath:containerPath imageId
```

## 挂载卷为容器

* 创建数据容器

``` bash
$ docker create --name containerdataName -v hostPath:containerPath imageId
或
$ docker container --name containerdataName -v hostPath:containerPath imageId
```

* 将数据容器作为挂载卷

``` bash
$ docker run --name containerName -d -p hostPort:containerPort -volumes-from dataContainerId imageId
或
$ docker container run --name containerName -d -p hostPort:containerPort -volumes-from dataContainerId imageId
```