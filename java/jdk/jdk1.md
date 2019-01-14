# <img src="../../images/icon/java.png" width="30" height="23" />Jdk安装

---

## Linux

* 进入官网【Java SE】版本选择页面[https://www.oracle.com/technetwork/java/javase/archive-139210.html](https://www.oracle.com/technetwork/java/javase/archive-139210.html)

![Jdk-Content](/images/java/jdk_content/Jdk-Content1.png)

* 点击选择对应的Java SE版本

![Jdk-Content](/images/java/jdk_content/Jdk-Content2.png)

* 选择下载开发环境（Java SE Development），点击【Accept License Agreement】，选择对应的安装包

![Jdk-Content](/images/java/jdk_content/Jdk-Content3.png)

* 跳转到登录页，输入用户名密码进行登录，登录成功后浏览器进行自动下载

![Jdk-Content](/images/java/jdk_content/Jdk-Content4.png)

* 下载完成后，上传至远程服务器

**需要将本机中的秘钥写入到远程服务器中的authorized_keys文件中，做服务器间的免密码文件传输使用，也可以使用密码进行scp传输**

![Jdk-Content](/images/java/jdk_content/Jdk-Content5.png)

```zsh
scp jdk-8u181-linux-x64.tar.gz root@${IP}:/Software/
```

* 上传完成之后，解压

```bash
tar -zxf jdk-8u181-linux-x64.tar.gz
```

* 配置环境变量

```bash
# 配置Java环境变量
export JAVA_HOME=/Software/jdk1.8.0_181
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export PATH=$PATH:$JAVA_HOME/bin
```

* 刷新环境变量

```bash
source /etc/profile
```

* 查看Java版本，确定安装完成

```bash
java -version
```