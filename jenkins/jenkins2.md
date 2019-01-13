# <img src="../images/icon/jenkins.svg" width="30" height="30" />Jenkins服务安装

---

## 使用Java环境

* 从官方下载War包，使用War包进行Jenkins的使用，下载地址：[https://jenkins.io/download/](https://jenkins.io/download/)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java1.png)

* 下载完成之后，将War包放到自己定义的工作目录中，然后使用java -jar命令进行启动，不指定端口号默认为8080，如果需要，可以在终端直接进行端口号的修改

> 终端启动命令

```zsh
java -jar jenkins.war --httpPort=8099
```

> 后台运行启动命令：使用nohup

```zsh
nohup java -jar jenkins.war --httpPort=8099 &
```

### 启动完成之后，开始Jenkins的基本配置，这里演示使用Mac OS环境

1.下载完成之后将Jar包放在我自己的 【SoftWare/Jenkins】 目录下，然后使用后台启动命令

![JenkinsConcept](../images/jenkins_content/Jenkins-Java2.png)

2.启动后，访问页面，进行Jenkins的初始化，Jenkins在第一次启动时候需要时间比较长，耐心等待

> 第一次登陆我们需要使用Jenkins生成的密码，系统会根据你的系统告诉你初始密码生成的位置，当然，
> 在启动日志中也会输出密码

![JenkinsConcept](../images/jenkins_content/Jenkins-Java3.png)

3.根据提示查看初始密码

![JenkinsConcept](../images/jenkins_content/Jenkins-Java4.png)

4.复制密码并继续

![JenkinsConcept](../images/jenkins_content/Jenkins-Java5.png)

5.这个时候正常来说应该跳转到安装插件页面，但是没有，如果Jenkins提示我们是离线状态的话，我们需要
更改一下他的某些配置，我们看一下日志是否正常

![JenkinsConcept](../images/jenkins_content/Jenkins-Java6.png)

> 查看日志

```zhs
tail -fn500 nohup.out
```

![JenkinsConcept](../images/jenkins_content/Jenkins-Java8.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java9.png)

> 日志中提示无法加载默认插件，并且抛出链接超时的异常，我们需要手动更改配置

6.在地址的后缀添加以下路径：【/pluginManager/advanced】，然后访问，进入设置页面

![JenkinsConcept](../images/jenkins_content/Jenkins-Java10.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java11.png)

> 将原来Update Site的https地址修改修改为http，点击submit保存

![JenkinsConcept](../images/jenkins_content/Jenkins-Java12.png)

7.杀掉进程，重新启动程序，访问Jenkins，再次查看并且输入密码，成功进入设置Jenkins界面

![JenkinsConcept](../images/jenkins_content/Jenkins-Java13.png)

8.选择建议安装的插件，等待插件安装完毕

> 如果出现插件安装失败，可以手动从官网进行插件下载，并进行上传，或重新进行Jenkins插件初始化

![JenkinsConcept](../images/jenkins_content/Jenkins-Java14.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java15.png)

9.安装完成后，设置基本信息（用户名、密码、名称、邮箱）、设置Jenkins访问地址

![JenkinsConcept](../images/jenkins_content/Jenkins-Java16.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java17.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java18.png)

10.重启项目，输入刚才设置的用户名、密码，然后开始使用Jenkins

![JenkinsConcept](../images/jenkins_content/Jenkins-Java19.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java20.png)

![JenkinsConcept](../images/jenkins_content/Jenkins-Java21.png)