---
title: "数据字典"
date: 2018-01-28T21:57:07+01:00
anchor: "dict"
weight: 40
---

## 数据字典


<table>
  <tr>
    <th width=20%, bgcolor=yellow >字段</th>
    <th width=20%, bgcolor=yellow>类型</th>
    <th width="60%", bgcolor=yellow>描述</th>
  </tr>
  <tr>
    <td> @timestamp </td>
    <td> date </td>
    <td> 字符串形式的时间戳，ES,Kibana使用 </td>
  </tr>
  <tr>
    <td> bodyb64 </td>
    <td> boolean </td>
    <td> 相应体是否使用base64处理（body传输时开启gzip会有此字段） </td>
  <tr>
    <td> cap_ip </td>
    <td> string </td>
    <td> 本记录抓取源网卡IP </td>
  </tr>
  <tr>
    <td> cap_source </td>
    <td> string </td>
    <td> 本记录抓取源网卡MAC地址 </td>
  </tr>
  <tr>
    <td> cap_timens </td>
    <td> number </td>
    <td> 本记录抓取时刻秒以下时间ns </td>
  </tr>
  <tr>
    <td> connectIP </td>
    <td> ip </td>
    <td> 连接者IP </td>
  </tr>
  <tr>
    <td> dst </td>
    <td> ip </td>
    <td> 目的地址IP </td>
  </tr>
  <tr>
    <td> extention </td>
    <td> string </td>
    <td> 请求文件(URI)扩展名 </td>
  </tr>
  <tr>
    <td> geo_city </td>
    <td> string </td>
    <td> 客户端地理位置-城市 </td>
  </tr>
  <tr>
    <td> geo_country </td>
    <td> string </td>
    <td> 客户端地理位置-国家 </td>
  </tr>
  <tr>
    <td> kafka_pid </td>
    <td> number </td>
    <td> 如果消息队列为kafka时, 本字段可以用来追踪消息均衡 </td>
  </tr>
  <tr>
    <td> raw_time </td>
    <td> date </td>
    <td> 从网卡抓取到的UTC时间戳 </td>
  </tr>
  <tr>
    <td> realIP </td>
    <td> ip </td>
    <td> 真实IP </td>
  </tr>
  <tr>
    <td> realUrl </td>
    <td> string </td>
    <td> 真实Url，不含参数 </td>
  </tr>

  <tr>
    <td> request.body </td>
    <td> string </td>
    <td> 请求体 </td>
  </tr>
  <tr>
    <td> request.content-encoding </td>
    <td> string </td>
    <td> 请求内容编码类型 </td>
  </tr>
  <tr>
    <td> request.content-type </td>
    <td> string </td>
    <td> 请求内容类型 </td>
  </tr>
  <tr>
    <td> request.cookie </td>
    <td> string </td>
    <td> 请求cookie </td>
  </tr>
  <tr>
    <td> request.host </td>
    <td> string </td>
    <td> 请求host </td>
  </tr>
  <tr>
    <td> request.method </td>
    <td> string </td>
    <td> 请求方法 </td>
  </tr>
  <tr>
    <td> request.referer </td>
    <td> string </td>
    <td> 请求referer </td>
  </tr>
  <tr>
    <td> request.user-agent </td>
    <td> string </td>
    <td> 请求UA </td>
  </tr>
  <tr>
    <td> request.x-forwarded-for </td>
    <td> string </td>
    <td> 请求x-forwarded-for </td>
  </tr>
  <tr>
    <td> response.body </td>
    <td> string </td>
    <td> 响应编码体 </td>
  </tr>
  <tr>
    <td> response.code </td>
    <td> number </td>
    <td> 响应HTTP代码 </td>
  </tr>
  <tr>
    <td> response.status </td>
    <td> number </td>
    <td> status代码 </td>
  </tr>
  <tr>
    <td> response.content-encoding </td>
    <td> string </td>
    <td> 响应体编码 </td>
  </tr>
  <tr>
    <td> response.content-type </td>
    <td> string </td>
    <td> 响应体类型 </td>
  </tr>
  <tr>
    <td> response.content-length </td>
    <td> string </td>
    <td> 响应体长度 </td>
  </tr>
  <tr>
    <td> response.location </td>
    <td> string </td>
    <td> 响应location </td>
  </tr>
  <tr>
    <td> src </td>
    <td> string </td>
    <td> 请求源地址IP </td>
  </tr>
  <tr>
    <td> tag </td>
    <td> string </td>
    <td> 标记 </td>
  </tr>
  <tr>
    <td> tag </td>
    <td> string </td>
    <td> 标签 </td>
  </tr>
  <tr>
    <td> time </td>
    <td> string </td>
    <td> 解析时刻时间 </td>
  </tr>
  <tr>
    <td> unix_time </td>
    <td> number </td>
    <td> 解析时刻时间 </td>
  </tr>

</table>




