---
title: "FAQ"
date: 2018-01-28T21:55:52+01:00
anchor: "FAQ"
weight: 50
---

## 常见问题

1. 怎么解决使用了HTTPS证书后无法获取加密的流量

		将HTTPS部署到反向代理上，通过反向代理之后卸载TLS流量；此时在通过在反向代理上利用端口过滤的方式拿出所需要的解密后的流量

2. 是否支持GZIP?

		支持，默认情况下，对于静态资源的response.body会被drop掉内容。对于超长的会截断内容

2. kafka资源数量估计(kafka分区数，kafka broker数量)

		每个请求平均为1k，那么TPS * 1k = 实时流量
		kafka broker数量 约等于 实时流量/kafka带宽/每机器分区数

3. ElasticSearch 资源需求

		ElasticSearch 内存限制了查询的数据量
		ElasticSearch 硬盘限制存储的数据量

4. 修改单机版ElasticSearch内存限制

		ps -ef 查看容器id
	
		进入docker容器 docker exec -it <id> /bin/sh
		kill elasticsearch进程
		修改/home/elasticsearch/elasticsearch/config/jvm.options文件字段:
		-Xmx=1G
		-Xms=1G
		保存后重新启动ElasticSearch
	
5. 过滤器

		目前端口过滤器用，在集群版里支持域名过滤器