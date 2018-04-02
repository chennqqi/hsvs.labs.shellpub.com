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
* 消息队列(推荐kafka, 如无可以使用redis替代)
* elasticsearch XPack插件(可选)

## 环境要求

* 镜像流量建议单独部署到物理机（根据实际情况内存需求>tps*3000 Byte)，如果流量过大需要使用网络分流器
* kafka使用企业公共资源 (partation,broker数量根据流量调整)
* ElasticSearch使用企业公共资源(节点>=3, 本系统通过ElasticSearch Gateway接入)


## 部署拓扑图

![](https://s1.ax1x.com/2018/04/02/CSPyuD.png)


## 获取程序

	集群-内网版还在开放当中...

	程序猿宝宝们正在紧急开发当中，留下您的联系方式，完成后第一时间通知您

<br>

<iframe src="http://www.shellpub.com/hsvs.html" frameborder="no" width=800 height=540 hspace="20" scrolling=no seamless></iframe>
