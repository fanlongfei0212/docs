# <img src="../../images/icon/springboot.jpeg" width="30" height="30" />多环境配置

---

**在开发应用时，我们需要通常有多个环境，比如开发、测试以及生产，这些不同环境中某些配置是不一样的，**
**如果在为不同环境打包时都要频繁修改配置文件的话，是一件很繁琐而且很容易出错的事**

## 不同环境不同文件

* **在SpringBoot中，多环境配置的文件名需要满足```application-{profile}.properties```的格式，其中```{profile}```对应你的环境标识**

    1. ```application-develop.properties```:开发环境
    
    2. ```application-test.propertis```:测试环境
    
    3. ```application-production.propertis```:生产环境

* **在```application.properties```文件中使用```spring.profiles.active=develop```指定对应的环境**

## 命令行参数

* **在启动java文件的时候指定环境配置```java -jar xxx.jar --spring.profiles.active=develop```**

## 多种方式使用

* **多种方式使用不同的环境配置文件**

    1. 在为不同的环境进行打包的时候，打包前在```application.properties```文件中使用```spring.profiles.active=```指定对应的环境
    
    2. 开发环境是我们使用最频繁的环境，那么我们可以再```application.properties```文件中以开发环境为默认配置```spring.profiles.active=develop```，在启动文件的时候通过命令行的方式去激活不同环境的配置```java -jar xxx.jar --spring.profiles.active=test```
    
## 加载顺序

* **为了能够更合理地重写个属性的值，SpringBoot使用了下面这种较为特别的属性加载顺序，优先级的顺序由高到低，数字越小优先级越高**

    1. 在命令行中传入的参数
    
    2. ```SPRING_APPLICATION_JSON```中的属性。```SPRING_APPLICATION_JSON```是以JSON格式配置在系统环境变量中的内容
    
    3. ```java:comp/env```中的JNDI属性
    
    4. Java的系统属性，可以通过```System.getProperties()```获得的内容
    
    5. 操作系统的环境变量
    
    6. 通过```random.*```配置的随机属性
    
    7. 位于当前应用jar包之外，针对不同```{profile}```环境的配置文件内容，例如```application-{profile}.properties```或是YAML定义的配置文件
    
    8. 位于当前应用jar包之内，针对不同```{profile}```环境的配置文件内容，例如```application-{profile}.properties```或是YAML定义的配置文件
    
    9. 位于当前应用jar包之外的```application.properties```和YAML配置内容
    
    10. 位于当前应用jar包之内的```application.properties```和YAML配置内容
    
    11. 在```@Configuration```注解修改的类中，通过```@PropertySource```注解定义的属性
    
    12. 应用默认属性，使用```SpringApplication.setDefaultProperties```定义的内容