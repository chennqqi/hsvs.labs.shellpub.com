---
title: "BUG追踪"
date: 2018-04-02T21:57:07+08:00
anchor: "bug"
weight: 45
---

## 单机版BUG追踪

id， bug编号
状态，是否已修复
计划, 修复计划
范围，受影响版本范围（单机版，集群版)

<table>
  <tr>
    <th width=10%, bgcolor=yellow >id</th>
    <th width=10%, bgcolor=yellow>状态</th>
    <th width=10%, bgcolor=yellow>范围</th>
    <th width=20%, bgcolor=yellow>计划</th>
    <th width="60%", bgcolor=yellow>描述</th>
  </tr>
  <tr>
    <td> 1 </td>
    <td bgcolor="#28A745"> 已修复 </td>
    <td> 所有版本 </td>
    <td> 已修复(>=1.1) </td>
    <td> 命令行启动-P模式不被识别 </td>
  </tr>
  <tr>
    <td> 2 </td>
    <td bgcolor="#28A745"> 已修复 </td>
    <td> 单机版 </td>
    <td> 已修复(>=1.1) </td>
    <td> 如果docker运行环境配置较差（例如超低配置的虚拟机），ES启动时间过久导致分析程序无法正常工作 </td>
  </tr>
  <tr>
    <td> 3 </td>
    <td bgcolor="#28A745"> 已修复 </td>
    <td> 单机版，集群-公网版 </td>
    <td> 已修复(>=1.2) </td>
    <td> 当前环境下抓到的包丢包率较大 </td>
  </tr>
  <tr>
    <td> 4 </td>
    <td bgcolor="#28A745"> 已修复 </td>
    <td> 单机版，集群-公网版 </td>
    <td> 已修复(>=1.2) </td>
    <td> request.body 无法处理被gzip压缩过的数据 </td>
  </tr>
  <tr>
    <td> 5 </td>
    <td bgcolor="#28A745"> 已修复 </td>
    <td> 单机版，集群-公网版 </td>
    <td> 已修复(>=1.2) </td>
    <td> release版程序抓包时空指针导致崩溃 </td>
  </tr>
</table>

## 集群BUG追踪
