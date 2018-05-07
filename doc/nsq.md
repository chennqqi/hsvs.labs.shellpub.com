# HSVS-nsq方案


<center>![](https://s1.ax1x.com/2018/04/02/CSA2sf.png)</center>


本文档适用于hcap:1.0,hsvs-mbridge:1.1.2 版本，此版本为当前latest分支

## 拓扑图



![](https://s1.ax1x.com/2018/05/07/CU4l5j.png)

<p style="color:green">绿色部分为HSVS提供</p>
<p style="color:blue">蓝色部分需要用户自己安装或者使用企业已有资源</p>



## 安装步骤


### 1. 安装部署ElasitcSearch 和 Kibana

版本要求**ElasticSearch(version >= 5.0.0)**

**建议优先使用企业已有的ElasticSearch资源**，这里给出一个[elasticsearch集群搭建博客教程](https://blog.csdn.net/chenxun_2010/article/details/78437852)

hsvs-mbridge 启动后会自动创建模板，无需手动创建索引和模板

### 2. 安装部署nsq

官方文档<https://nsq.io/overview/design.html>

每一台数据抓取点(hcap)的机器上均需要部署[nsqd](<https://nsq.io/components/nsqd.html>)

在抓取点之外选择2-3台机器部署[nsqlookupd](https://nsq.io/components/nsqlookupd.html)
和[nsqadmin](https://nsq.io/components/nsqadmin.html)

通过nsqadmin或者命令行创建nsq的topic

![](https://s1.ax1x.com/2018/05/06/CUdCWj.png)


### 3. 安装部署hsvs-mbridge

本程序是数据预处理模块，会将处理后的数据写入ElasticSearch。
本程序部署数量跟第2部中设定的kafka数量有关。需被整除，即hsvs-mbridge的部署数量乘以N(N为正整数)等于kafka创建的分区数。


- 拉取镜像, 如果您内网的机器无法联网，可以使用docker save/load的方式导入到您的机器上

	docker pull hsvs-mbridge


- 下载配置文件模板，修改成您实际环境中的配置

	wget labs.shellpub.com/hsvs/mbridge.yml


- 配置文件说明



  * nsq 字段配置与redis相关属性

			nsqlookupd_addrs: [ "10.0.0.1:4161","10.0.0.2:4161" ] #填写nsqlookup集群地址
			nsq_topic: "http_session"


  * es_config 字段配置与elasticsearch有关属性

		  	es_host: "填写ElasticMaster Node的IP地址"

  * source: 字段设定数据源，使用nsq时，此处应该填写"nsq"


我们假定您的配置文件存储路径位于/opt/mbridge.yml

* 启动mbridge

		docker run --net=host --rm -e ELASTICSEARCH_URL=http://<YOUR_ES_MASTER_HOST>:9200/ -v /opt/mbridge.yml:/hsvs/mbridge/mbridge.yml:ro sort/hsvs-mbridge

此处必须指定ELASTICSEARCH_URL传递ElasticSearch地址给hsvs-mbridge，来创建template模板


### 4. 安装部署hcap

本程序是http流还原模块，应当不属于镜像流量或者http反向代理机上


拉取镜像 
	
	docker pull sort/hcap

下载配置文件模板, 修改成您实际环境中的配置

	wget labs.shellpub.com/hsvs/hcap.ini


配置文件关键配置说明

	[MAIN]
	NIC_name = eth0 # 网卡名称
	promisc = 0 # 是否开启混杂模式，镜像流量模式必须，反向代理模式下无须开启
	output_target = kafka # 写入目标，使用kafaka时此处必须配置为kafka
	
	[FILTER]
	include_domains = * # 过滤域名，支持通配语法
	#exclude_domains = # 排除域名
	
	[OUTPUT_NSQ]
	host=127.0.0.1 # 因为是在每台hcap抓取点部署，所以均填写127.0.0.1
	port=4150
	topic=http_session
	
运行hcap， 我们假定您的配置文件路径位于/opt/hcap.ini

	docker run --net=host --privileged -d -v /opt/hcap.ini:/hsvs/hcaplite/hcap.ini:ro --rm sort/hcap -Bb -i eth0	

	参数说明:
		-Bb 获取请求题和响应体
		-i 非必须，指定您所需抓包网卡名称，本参数会覆盖配置文件中的Nic_Name字段
		
	
### 5. 打开kibana创建kibana 索引


		启动时间大约为1分钟后，系统中抓取到记录后打开kibana  
		http://<你的KIBNA主机IP>:5601  
		点击左侧导航栏->Management->Index Patterns->Create Index Pattern
		在Index name or pattern中输入
		logstash-http-session-*
		在下面`Time Filter field name`中选择@timestamp
		点击Create完成创建, 下面两个[DEPRECATED]选项不要勾选！
		点击左侧导航栏Discover即可查看抓取到的流量

![](https://s1.ax1x.com/2018/04/05/C9b4VP.png)
	
