# <img src="../../images/icon/springcloud.png" width="30" height="23" />SpringCloud

---

**SpringCloud是一个基于SpringBoot实现的微服务架构开发工具。它为微服务架构中涉及的配置管理、服务治理**
**、断路器、智能路由、微代理、控制总线、全局锁、决策竞选、分布式会话和集群状态管理等操作提供了一种简单的开发方式。**

<img src="../../images/icon/springcloud.png" width="180" height="140" />

## 简介

* **SpringCloudConfig:配置管理工具，支持使用Git存储配置内容，可以使用它实现应用配置的外部化存储，并支持客户端配置信息刷新、**
**加密/解密配置内容等。**

* **SpringCloudNetflix:核心组件，对多个Netflix 0SS开源套件进行整合。**

    1. Eureka：服务治理组件，包含服务注册中心、服务注册与发现机制的实现。
    
    2. Hystrix：容错管理组件，实现断路器模式，帮助服务依赖中出现的延迟和为故障提供强大的容错能力。
    
    3. Ribbon：客户端负载均衡的服务调用组件。
    
    4. Fegin：基于Ribbon和Hystrix的声明式服务调用组件。
    
    5. Zuul：网关组件，提供智能路由、访问、过滤等功能。
    
    6. Archaius：外部化配置组件。

* **SpringCloudBus：事件、消息总线，用于传播集群中的状态变化或事件，以及触发后续的处理，比如用来动态刷新配置等。**

* **SpringCloudCluster：针对Zookeeper、Redis、Hazelcast、Consul的选举算法和通用状态模式的实现。**

* **SpringCloudCloudfoundry：与PivotalCloudfoundry的整合支持。**

* **SpringCloudConsul：服务发现与配置管理工具。**

* **SpringCloudStream：通过Redis、Rabbit或者Kafka实现的消费微服务、可以通过简单的声明式模型来发送和接收消息。**

* **SpringCloudAWS：用于简化整合AmazonWebService组件。**

* **SpringCloudSecurity：安全工具包，提供在Zuul代理中对OAuth2客户端请求的中继器。**

* **SpringCloudSleuth：SpringCloud应用的分布式跟踪实现，可以完美整合Zipkin。**

* **SpringCloudZookeeper：基于Zookeeper的服务发现与配置管理组件。**

* **SpringCloudStarters：SpringCloud的基础组件，它是基于SpringBoot风格项目的基础依赖模块。**

* **SpringCloudCLI：用于在Groovy中快速创建SpringCloud应用的SpringBootCLI插件。**