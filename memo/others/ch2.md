# 随笔

[TOC]

## 思考

1. 什么时候用RPC，什么时候用消息队列作为分布式系统的通讯手段
2. 使用MQ作为通讯手段，消息的大小有限制，体积过大的消息不适合使用MQ，那么有类似需求时如何传递
3. 响应式带来什么样的好处，适用场景有哪些，运用原则是什么

## 待填的坑

1. 参考有赞开源的基于gatling的dubbo全链路测试插件定制自己的测试工具

## 问题

1. 按照rocketMQ的官方示例写的异步发送测试代码，生产者会报告`No route info of this topic`([传送门](./ch2/problems/p1.md))
2. 使用Spring Boot加载yml格式的配置时出现无法匹配`propertyPlaceHolder`的情况([传送门](./ch2/problems/p2.md))
3. 编写自用模块的starter实现自动配置时，自动配置无法生效，正确的做法是什么？([传送门](./ch2/problems/p3.md))
4. 适用gatling对项目进行测试，遇到`illegal cyclic inheritance involving trait Iterable`以及`no such method`怎么办([传送门](./ch2/problems/p4.md))
