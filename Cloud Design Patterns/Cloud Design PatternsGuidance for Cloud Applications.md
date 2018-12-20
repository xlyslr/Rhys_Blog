---
title: 云设计模式：云应用的规范架构指南
date: 2018-12-19
source-title: Cloud Design Patterns: Prescriptive Architecture Guidance for Cloud Applications
source: https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn568099(v%3dpandp.10)
---

该指南包含24中设计模式和10个相关的指导主题，通过展示如何将每一部分融入到云应用体系结构的蓝图中，来阐明使用设计模式的好处。此外，还讨论了每种设计模式的好处和注意事项。大多数设计模式都提供了[代码示例](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn622075%28v%3dpandp.10%29)或代码片段，来说明如何使用Microsoft Azure的特性实现。不管怎样，该指南中描述的大多数主题同样适用于所有类型的分布式系统，无论是在Azure上，还是其他云平台上。

# 设计模式

下面描述的设计模式在云托管的应用程序中非常有用。每种设计模式都以一种通用的方式提供：描述上下文和问题、解决方案、使用该设计模式的问题及注意事项，以及一个基于Azure的示例。此外，还提供了相关设计模式的链接。每个项目顶部的图标标明了涉及的[问题领域](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn589772%28v%3dpandp.10%29)。有些设计模式有代码示例，你可以一次下载所有[代码示例](https://docs.microsoft.com/zh-cn/previous-versions/msp-n-p/dn622075%28v%3dpandp.10%29)，也可以单击![](assets/sample_code.png)，下载该模式的示例。

> 备注
>
> 我们的意图不是提供一个全面的设计模式集合。相反，我们选择了我们认为对云应用有用的设计模式，并考虑到每个设计模式在用户中的受欢迎程度。这也不是关于Azure特征的详细指南。

## 旁路缓存模式（Cache-aside Pattern）

![Data Management](assets/datamanagement.png) ![Performance & Scalability](assets/performance.png)![Design Patterns](assets/design_pattern.png) 

根据需要从数据存储区将数据加载到缓存中。这种模式可以提高性能，并有助于保持缓存与基础数据存储区的数据一致性。

![Cache-aside Pattern](assets/dn568099.cache-aside(en-us,pandp.10).png) 

## 断路器模式（Circuit Breaker Pattern）

![Resiliency](assets/resilience.png) ![Design Patterns](assets/design_pattern.png)

处理连接到远程服务或资源的故障时，需要的时间不可控。这种模式可以提高应用程序的稳定性和弹性。

 ![Circuit Breaker Pattern](assets/dn568099.circuit_breaker(en-us,pandp.10).png) 

## 交易补偿模式（Compensating Transaction Pattern）

![Resiliency](assets/resilience.png) ![Design Patterns](assets/design_pattern.png)

如果一个或多个操作失败，通过一系列保证最终一致性的操作，来抵消影响。实现复杂业务流程和工作流程的云托管应用中，通常可以找到这种遵循最终一致性模型的操作。

![Compensating Transaction Pattern](assets/dn568099.compensating_transaction(en-us,pandp.10).png) 

## 竞争消费者模式（Competing Consumers Pattern）

![Messaging](assets/messaging.png)![Performance & Scalability](assets/performance.png)![Design Patterns](assets/design_pattern.png)![Download code sample](assets/sample_code.png)

让多个消费者同时在同一消息通道上接收消息。这种模式能够使系统同时处理多条消息，以优化吞吐量，提高伸缩性和可用性，并平衡负载。

![Competing Consumers Pattern](assets/dn568099.competing_consumers(en-us,pandp.10).png)

## 计算资源整合模式（Compute Resource Consolidation Pattern）

![Design and Implementation](assets/design_dev.png)![Design Patterns](assets/design_pattern.png)![](assets/sample_code.png)

将多个任务或操作整合到一个计算单元中。这种模式可以提高计算资源利用率，并减少在云托管应用中执行计算相关的成本和管理开销。

![Compute Resource Consolidation Pattern](assets/dn568099.compute_resource_consolidation(en-us,pandp.10).png)

## 命令和查询职责分离模式（Command and Query Responsibility Segregation (CQRS) Pattern）

![](assets/datamanagement.png)![](assets/design_dev.png)![](assets/performance.png)![](assets/design_pattern.png)

使用独立的接口将读取数据和更新数据的操作隔离开。这种模式可以最大限度地提高性能、可伸缩性和安全性；通过更高的灵活性支持系统随时间的演变；并防止更新命令在领域级别造成合并冲突。

![CQRS Pattern](assets/dn568099.cqrs(en-us,pandp.10).png)

## 事件源模式（Event Souring Pattern）

![](assets/datamanagement.png)![](assets/performance.png)![](assets/design_pattern.png)

通过事件描述对领域中数据的处理，使用`append-only`存储来记录事件的完整序列，而不是只存储当前状态，从而可以使用存储来实现领域对象。这种模式可以通过避免同步数据模型和业务领域的要求，来简化复杂领域中的任务；提高性能、伸缩性和响应效率；为事务性数据提供一致性；并维护完整的审计路径和历史记录，来支持补偿动作。

![Event Sourcing Pattern](assets/dn568099.event_sourcing(en-us,pandp.10).png)

## 外部配置存储模式（External Configuration Store Pattern）

![](assets/design_dev.png)![Management and Monitoring](assets/manage_monitor.png)![](assets/design_pattern.png)![](assets/sample_code.png)

将配置信息从应用程序部署包移动到集中位置。这种模式可以更容易地管理配置信息，并能在应用程序之间和应用实例之间共享配置信息。

![External Configuration Store Pattern](assets/dn568099.external_configuration_store(en-us,pandp.10).png)

## 联合身份模式（Federated Identity Pattern）

![Security](assets/security.png)![](assets/design_pattern.png)

将身份认证委托给外部身份程序。这种模式可以简化开发，最小化用户管理需求，并改善应用的用户体验。

![Federated Identity Pattern](assets/dn568099.federated_identity(en-us,pandp.10).png)

## 守门员模式（Gatekeeper Pattern）

![Security](assets/security.png)![](assets/design_pattern.png)

通过使用专用主机实例保护应用程序和服务，该实例充当客户端和应用程序或服务之间的代理，验证、净化请求，并在它们之间传递数据。这种模式可以提供一个额外的安全层，并限制系统的攻击面。

![Gatekeeper Pattern](assets/dn568099.gatekeeper(en-us,pandp.10).png)

## 端点健康监控模式（Health Endpoint Monitoring Pattern）

![Availability](assets/availability.png)![](assets/manage_monitor.png)![](assets/design_pattern.png)![](assets/sample_code.png)

在应用程序中实现功能检查，外部工具可以定期通过公开的端点进行访问。这种模式可以帮助验证应用程序和服务是否正确运行。

![Health Endpoint Monitoring Pattern](assets/dn568099.health_endpoint_monitoring(en-us,pandp.10).png)

## 索引表模式（Index Table Pattern）

![](assets/datamanagement.png)![](assets/performance.png)![](assets/design_pattern.png)

在查询条件经常引用的字段上创建索引。这种模式使得应用程序更快的从数据存储区检索数据，从而提高查询新能。

![Index Table Pattern](assets/dn568099.index_table(en-us,pandp.10).png)

## 领导者选举模式（Leader Election Pattern）

![](assets/design_dev.png)![](assets/resilience.png)![](assets/design_pattern.png)![](assets/sample_code.png)

通过选择一个实例作为负责管理其他实例的领导者，协调分布式应用程序中协作任务实例所执行的操作。这种模式可以确保任务之间不会发生冲突，导致共享资源的争抢，或者无意中干扰了其他任务实例正在执行的工作。

![Leader Election Pattern](assets/dn568099.leader_election(en-us,pandp.10).png)

## 物化视图模式（Materialized View Pattern）

![](assets/datamanagement.png)![](assets/performance.png)![](assets/design_pattern.png)

当数据以不利于所需查询操作的方式格式化时，在一个或多个数据存储中对数据生成预填充（pre-populated）的视图。这种模式可以帮助提高查询和数据提取的效率，并提高应用程序性能。

![Materialized View Pattern](assets/dn568099.materialized_view(en-us,pandp.10).png)

## 管道和过滤器模式（Pipes and Filters Pattern）

![](assets/messaging.png)![](assets/design_dev.png)![](assets/design_pattern.png)![](assets/sample_code.png)

将复杂的任务处理过程分解为一系列可重用的、不相关的元素。这种模式通过支持独立部署执行处理的任务元素，可以提高性能、可伸缩性和可重用性。

![Pipes and Filters Pattern](assets/dn568099.pipes_and_filters(en-us,pandp.10).png)

## 优先级队列模式（Priority Queue Pattern）

![](assets/messaging.png)![](assets/performance.png)![](assets/design_pattern.png)![](assets/sample_code.png)

按优先级处理发送给服务的请求，以便高优先级的请求可以比低优先级的被更快地接受并处理。在为不同类型的客户端提供不同级别的服务保证的应用程序中，这种模式非常有用。

![Priority Queue Pattern](assets/dn568099.priority_queue(en-us,pandp.10).png)

## 基于队列的负载均衡模式（Queue-based Load Leveling Pattern）

![](assets/messaging.png)![](assets/availability.png)![](assets/performance.png)![](assets/design_pattern.png)

使用队列作为任何和它调用的服务之间的缓冲区，以平滑间歇性的高负载，否则可能会导致服务失败或超时。这种模式和可以帮助最小化请求高峰对任务及服务可用性和响应性的影响。

![Queue-based Load Leveling Pattern](assets/dn568099.queue-based_load_leveling(en-us,pandp.10).png)

## 重试模式（Retry Pattern）

![](assets/resilience.png)![](assets/design_pattern.png)

连接服务或网络资源时，可以通过透明地重试操作来处理临时故障，这里的故障要求是短暂性的。这种模式可以提高应用程序的稳定性。

![Retry Pattern](assets/dn568099.retry(en-us,pandp.10).png)

## 运行时配置模式（Runtime Reconfiguration Pattern）

![](assets/design_dev.png)![](assets/manage_monitor.png)![](assets/design_pattern.png)![](assets/sample_code.png)

设计一个应用程序，可以在运行时重新配置，而不需要重新部署或重新启动。这种模式可以帮助保持可用性和最小化停机时间。

![Runtime Reconfiguration Pattern](assets/dn568099.runtime_reconfiguration(en-us,pandp.10).png)

## 调度器代理监督模式（Scheduler Agent Supervisor Pattern）

![](assets/messaging.png)![](assets/resilience.png)![](assets/design_pattern.png)

在一组分布式服务和其他远程资源之间协调一组操作，尝试在任何操作失败时透明地处理故障，或者在无法从故障中恢复时消除已执行工作的影响。这种模式可以通过恢复和重试由于短暂异常、持久故障和进程故障而失败的操作，从而提高分布式系统的弹性。

![Scheduler Agent Supervisor Pattern](assets/dn568099.scheduler_agent_supervisor(en-us,pandp.10).png)

## 分片模式（Sharding Pattern）

![](assets/datamanagement.png)![](assets/performance.png)![](assets/design_pattern.png)

将数据存储划分为一组水平分隔的分片。当存取大量数据时，这种模式可以提高可伸缩性。

![Sharding Pattern](assets/dn568099.sharding(en-us,pandp.10).png)

## 静态内容托管模式（Static Content Hosting Pattern）

![](assets/datamanagement.png)![](assets/design_dev.png)![](assets/performance.png)![](assets/design_pattern.png)![](assets/sample_code.png)

将静态内容部署到基于云的存储服务中，该服务可以将这些内容直接交付给客户端。这种模式可以减少对昂贵的计算实例的潜在需求。

![Static Content Hosting Pattern](assets/dn568099.static_content_hosting(en-us,pandp.10).png)

## 节流模式（Throttling Pattern）

![](assets/availability.png)![](assets/performance.png)![](assets/design_pattern.png)

控制应用实例、单租户或整个服务所使用的资源的消耗。这种模式可以使系统继续运行并满足服务等级协议，即使请求增长对资源带来极大的负载。

![Throttling Pattern](assets/dn568099.throttling(en-us,pandp.10).png)

## 

