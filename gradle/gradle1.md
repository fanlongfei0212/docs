# <img src="../../images/icon/gradle.png" width="30" height="23" />Gradle安装

---

## 安装Gradle环境

**Gradle的使用需要Java版本在1.8以及以上**

* 进入Gradle官网版本选择页面[https://gradle.org/releases/](https://gradle.org/releases/)

![Gradle-Install](/images/gradle_content/Gradle-Install1.png)

* 选择对应的版本，点击complete下载完整的Gradle或者使用【wget】直接下载

**在官方网站进行下载**

![Gradle-Install](/images/gradle_content/Gradle-Install2.png)

**使用wget命令进行下载**

```bash
https://downloads.gradle.org/distributions/gradle-4.5-all.zip
```

* 下载完成之后，解压

```bash
unzip gradle-4.5-all.zip
```

* 配置环境变量

```bash
# 配置Gradle环境变量
GRADLE_HOME=/Software/gradle-4.5
export PATH=${GRADLE_HOME}/bin:${PATH}
```

* 刷新环境变量

```bash
source /etc/profile
```

* 查看Gradle版本，确定安装完成

```bash
gradle -v
```