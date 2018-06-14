# <img src="../../images/icon/springboot.jpeg" style="zoom:8%" />SpringBoot

---

**
SpringBoot提供了一种新的编程范式，简化了Spring的许多样版式配置
**

<img src="../../images/icon/springboot.jpeg" style="zoom:70%" />

## 命令行界面

SpringBootCLI命令行可以快速的进行应用程序开发

## 起步依赖

spring-boot-starter

## 自动配置

根据SpringBoot指定的依赖，SpringBoot内部会进行条件化配置，看起来我们不需要指定一些一些配置类，那是SpringBoot
根据我们加入的依赖进行自动判断应该进行哪些初始化配置，比如springMvc的配置、视图配置以及jpa的配置等等，这是SpringBoot
能够进行自动配置的原因

## 自定义配置

当我们需要使用一些特定的配置，不想去使用SpringBoot提供的通过指定的依赖进行的自动化配置的时候，我们有两种选择，
一种是使用显示的配置进行覆盖SpringBoot提供的自动配置，还有一种就是使用属性去精细SpringBoot的配置

## 属性注入

可以使用@ConfigurationProperties(prefix="xxx")进行属性注入，可以注入application.properties、application.yml支持的任一属性源位置

## 不同环境下的不同配置

使用@Profile进行不通环境下的配置 开启/关闭
在类头使用@Profile("production")指定某些配置类只有在指定的环境中（比如：application.properties中使用spring.profiles.active=production）进行开启

## Actuator

## 资源

* SpringBoot CLI 下载地址

[http://repo.spring.io/release/org/springframework/boot/spring-boot-cli/](http://repo.spring.io/release/org/springframework/boot/spring-boot-cli/)