---
title: "简介"
date: 2018-04-02T15:42:17+08:00
anchor: "introduce"
weight: 10
---

本项目名称为HSVS(HTTP STREAM VISUALIZATION SYSTEM), HTTP流量可视化系统。 本项目名称为HSVS，并没有直接称呼为流量分析系统；目的是将分析部分开放出来，让使用者使用自己的方法，自由的进行分析。

HTTP全流量分析目前已经在各大厂里比较普及了(BAT，携程，网易...)。 HTTP全流量分析相比之前单纯的WEB日志多了详细的请求头，完整的相应体，能分析出更多有用的东西。特别是随着[RESTful](https://en.wikipedia.org/wiki/Representational_state_transfer)的流行，传统的WEB日志已经拿不到请求的真实响应(status code)了。 

全流量分析涉及到一定的底层开发，还有分析系统开发，对于小企业有一定门槛，本项目旨在消除此门槛，让大家都能做到自由的获取HTTP全流量数据。 笔者所从事的信息安全行业对于HTTP全流量分析需求比较迫切。 HTTP流量分析既可以发现信息安全领域的问题，也可以在业务风控领域有所建树。 从信息安全的发展趋势来看，目前是从信息安全往企业安全和内容安全发展。 而HTTP全流量分析成为了企业安全和内容安全的重要组成部分。 

{{% block note %}}

在使用本系统前建议了解的知识  
1. [ELK](https://www.elastic.co)  
2. [HTTP规范](https://www.w3.org/Protocols/rfc2616/rfc2616-sec8.html)  
3. 建议掌握一些常见的kibana搜索知识(简单使用)  
4. 掌握常用分析算法和分析程序（例如使用spark进行分析）  


{{% /block %}}
