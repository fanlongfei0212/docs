# <img src="../images/icon/docker.jpeg" width="30" height="30" />Docker 安装

---

## Mac OS

* 进入官网中docker的Mac版本获取中心:

[https://store.docker.com/editions/community/docker-ce-desktop-mac](https://store.docker.com/editions/community/docker-ce-desktop-mac)

>选择Stable channel版本或Edge channel版本

## Windows

* 进入官网中docker的Windows版本获取中心:

[https://store.docker.com/editions/community/docker-ce-desktop-windows](https://store.docker.com/editions/community/docker-ce-desktop-windows)

>选择Stable channel版本或Edge channel版本

## CentOS

* 设置yum

```bash
$ sudo yum install -y yum-utils \
  device-mapper-persistent-data \
  lvm2
```

```bash
$ sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
```

* 安装最新版本的docker-ce

``` bash
$ sudo yum install docker-ce
```

* 安装指定版本的docker-ce

``` bash
$ sudo yum install docker-ce-<VERSION STRING>
```

* 安装完成之后启动docker

>service命令:

``` bash
$ sudo service docker start
```

>systemctl命令:

``` bash
$ sudo systemctl start docker
```

* 安装完成之后执行命令，验证docker是否安装成功

``` bash
$ docker version
或
$ docker info
```

* 卸载docker包

``` bash
$ sudo yum remove docker-ce
```
* 卸载docker包并且删除image、container、volumes

``` bash
$ sudo rm -rf /var/lib/docker
```

* Docker需要用户具有root权限，如果是非root用户操作，除了在docker命令前加上sudo这种方式以外，还可以将当前操作docker的用户添加到docker用户组

``` bash
$ sudo usermod -aG docker userName
```

