---
title: "业务"
date: 2018-04-02T21:55:52+08:00
anchor: "work"
weight: 40
---

本文档重点不是kibana的使用教程，只是举了几个kibana使用的例子。

## 业务场景

1.使用Kibana分析请求量及其变化趋势

 		在kibana->Visualize 点击+号新建 Vertical Bar
		选择logstash-http-session-* index
		在Split Series中选择Date Historgram作为聚合方式


![](https://s1.ax1x.com/2018/04/02/CSiRLF.png)

2.使用kibana分析各域名访问量

		在kibana->Visualize 点击+号新建 Pie
		选择logstash-http-session-* index
		在Split Slices中选择terms作为聚合方式， 并选择request.host作为Field

![](https://s1.ax1x.com/2018/04/02/CSi6zV.png)

3.使用kibana分析HTTP服务状态比例

		在kibana->Visualize 点击+号新建 Pie
		选择logstash-http-session-* index
		在Split Slices中选择terms作为聚合方式， 并选择response.code作为Field

![](https://s1.ax1x.com/2018/04/02/CSi2sU.png)


4. 分析各个城市活跃量(地图)

	 	在kibana->Visualize 点击+号新建 Coordinate Map
		选择logstash-http-session-* index
		在Geo Coordinates 选择geo_location作为地图坐标


![](https://s1.ax1x.com/2018/04/02/CSifZ4.png)

在kibana vi

5. 分析请求量TOP N的接口

6. 分析请求量TOP N的客户端IP

7. 其他...