---
title: 云设计模式：云应用的规范架构指南
date: 2018-12-19
source-title: Cloud Design Patterns: Prescriptive Architecture Guidance for Cloud Applications
source: https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn568099(v%3dpandp.10)
---

该指南包含24中设计模式和10个相关的指导主题，通过展示如何将每一部分融入到云应用体系结构的蓝图中，来阐明使用设计模式的好处。此外，还讨论了每种设计模式的好处和注意事项。大多数设计模式都提供了[代码示例](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn622075%28v%3dpandp.10%29)或代码片段，来说明如何使用Microsoft Azure的特性实现。不管怎样，该指南中描述的大多数主题同样适用于所有类型的分布式系统，无论是在Azure上，还是其他云平台上。

# 设计模式

下面描述的设计模式在云托管的应用程序中非常有用。每种设计模式都以一种通用的方式提供：描述上下文和问题、解决方案、使用该设计模式的问题及注意事项，以及一个基于Azure的示例。此外，还提供了相关设计模式的链接。每个项目顶部的图标标明了涉及的[问题领域](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn589772%28v%3dpandp.10%29)[。有些设计模式有代码示例，你可以一次下载所有[代码示例](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn622075%28v%3dpandp.10%29)，也可以单击代码示例图标，下载该模式的示例。

> 备注
>
> 我们的意图不是提供一个全面的设计模式集合。相反，我们选择了我们认为对云应用有用的设计模式，并考虑到每个设计模式在用户中的受欢迎程度。这也不是关于Azure特征的详细指南。

## 旁路缓存模式（Cache-aside Pattern）

![Data Management](assets/datamanagement.png) ![Performance & Scalability](assets/performance.png)![Design Patterns](assets/design_pattern.png) 

根据需要从数据存储区将数据加载到缓存中。这种模式可以提高性能，并有助于保持缓存与基础数据存储区的数据一致性。

![Cache-aside Pattern](assets/dn568099.cache-aside(en-us,pandp.10).png) 

更多信息，请参考[旁路缓存模式](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn589799%28v%3dpandp.10%29)。

## 断路器模式（Circuit Breaker Pattern）

![Resiliency](assets/resilience.png) ![Design Patterns](assets/design_pattern.png)

处理连接到远程服务或资源的故障时，需要的时间不可控。这种模式可以提高应用程序的稳定性和弹性。

 ![Circuit Breaker Pattern](assets/dn568099.circuit_breaker(en-us,pandp.10).png) 

更多信息，请参考[断路器模式](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn589784%28v%3dpandp.10%29)。

## 交易补偿模式（Compensating Transaction Pattern）

![Resiliency](assets/resilience.png) ![Design Patterns](assets/design_pattern.png)

如果一个或多个操作失败，通过一系列保证最终一致性的操作，来抵消影响。实现复杂业务流程和工作流程的云托管应用中，通常可以找到这种遵循最终一致性模型的操作。

![Compensating Transaction Pattern](assets/dn568099.compensating_transaction(en-us,pandp.10).png) 

更多信息，请参考[交易补偿模式](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn589804%28v%3dpandp.10%29)。

## 竞争消费者模式（Competing Consumers Pattern）