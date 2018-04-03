---
title: "单机版"
date: 2018-04-02T21:48:10+08:00
anchor: "install_standalone"
weight: 20
---

## 适用场景

业务量较小的网站或者公司，完整集成包，开箱即用。

## 需求

1. 空闲内存>1.5GB (内置ES内存限制为1G， 如果内存较大可以手动修改，配置不要超过系统内存的一半)
2. tps < 3000
3. cpu核心数>=2


## 部署方式

1.流量镜像模式；  

![](https://s1.ax1x.com/2018/04/02/9z5bWt.png)

2.直接在反向代理部署, 确保你的反向代理开启了X_FORWARD_FOF；  

![](https://s1.ax1x.com/2018/04/02/9z5HJI.png)

3.如果使用了HTTPS，可以结合1，2两种方案进行, 在反向代理抓取HTTPS卸载之后的流量，在镜像抓取纯HTTP流量  


## 依赖

* [docker](http://www.docker.org.cn/book/docker/what-is-docker-16.html)


## 获取程序

	docker  pull sort/hsvs-standalone:kibana5

## 运行说明

1. 首先应当在您的环境下安装Docker

2. 拉取镜像

	docker pull sort/hsvs-standalone:kibana5

3. 运行

```python
	
	docker run -d --privileged=true --net=host -p 5601:5601 -p 9200:9200 sort/hsvs-standalone:kibana5 -f 'tcp port 80' -i eth0 -P

```

	docker参数说明
		
		-d 让docker镜像以后台守护进程的方式运行
		-p docker 端口，将docker内部的kibana和elasticsearch端口映射到主机
		--privilged=true 开启root权限，允许docker程序抓包
		--net=host 使用主机网络，这样docker里程序可以抓取主机流量
		
	运行参数说明
	
		-i <ethname> 指定网卡名称 
		-f <port filter> 可选， 指定过滤端口信息，如果不加此选项默认会处理所有端口，这个选项在https反代抓包时很有用，过滤器语法同tcpdump语法
		-P 可选，开启混杂模式，在流量镜像模式抓包时使用，在主机抓包时请不要使用此选项

4. 打开kibana即可访问

	单机版启动时间大约为1分钟

	


		