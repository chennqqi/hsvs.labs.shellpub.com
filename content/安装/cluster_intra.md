---
title: "集群-内网版*"
date: 2018-01-28T21:48:10+01:00
anchor: "cluster_intra"
weight: 20
---


## 适用场景

企业内网，IDC机房。
可以采用两种部署模式：  
1. 流量镜像模式；  
2. 直接在反向代理部署；  
3. 如果使用了HTTPS，可以结合1，2两种方案进行  


## 依赖

* docker
* elasticsearch(建议版本>=5.0)
* kibana(建议版本>=5.0)
* 消息队列(推荐kafka, 如无可以使用redis/nsq替代)
* elasticsearch XPack插件(可选)

## 环境要求

* 镜像流量建议单独部署到物理机（根据实际情况内存需求>tps*3000 Byte)，如果流量过大需要使用网络分流器
* 消息中间件kafka (可选nsq和redis)
* ElasticSearch 集群


## 节点描述

* hcap 抓取模块，负责将http流还原成json数据
* 消息中间件(kafka/nsq/redis)
* mbridge，负责将json数据从消息中间件中处理写入ElasticSearch
* ElasticSearch + kibana 最终的消息存储和可视化的显示
* analyzed(尚未开发完成) 负责实时分析流量，根据配置的（安全或者风控）规则出处命中结果到ElasticSearch

## 方案一(强烈建议), 使用kafka消息中间件部署拓扑图

优点: kafka吞吐率，稳定性，持久化很优秀，经过长期实践检验，kafka可以多group消费者同时消费一topic数据，方便自定义开发分析程序

缺点: kafka部署较为麻烦，优先选择企业内部已经搭建好的kafka，最新版的kafka已经集成了zookeeper，如果需要自己搭建请参考<http://kafka.apache.org/quickstart>


![](https://s1.ax1x.com/2018/04/02/CSPyuD.png)

## 方案二， 使用nsq消息中间件部署拓扑图

优点: nsq是一个golang开发的消息中间件，部署简单，使用也简单，支持持久化，支持多group消费者消费同一topic数据。

缺点: nsq设计理念是本地agent，所以如果在镜像流量机器上部署Agent容易出现吞吐率不够的问题。


## 方案三， 使用redis做消息中间件部署拓扑图

优点: 部署简单，可以使用企业已有redis

缺点: 目前hcap不支持写入集群，redis不支持多group订阅消费，无法自定义分析程序，且不支持持久化。


## 获取程序


<br>

<iframe src="http://www.shellpub.com/hsvs.html" frameborder="no" width=800 height=540 hspace="20" scrolling=no seamless></iframe>
