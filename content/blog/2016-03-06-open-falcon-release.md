---
title: Open-Falcon v0.1.0 Release
created_at: 2016-03-06
kind: article
author_name: Lai Wei
---

http://www.jianshu.com/p/7751eb324a51

OpenFalcon是一个开源的、企业级的、高可用、可扩展的监控系统，最早由小米运维团队发起和开源，目前已经成为国内互联网公司使用最广泛的监控系统之一；并形成了良好的开源社区和用户基础，积累了一批核心的社区开发成员；目前活跃社区成员2000+，核心开发成员来自小米、美团、快网、滴滴等多家公司。

距离上一个小版本的发布，已经过去有大半年的时间了，经过OpenFalcon社区的辛苦付出，终于迎来了v0.1.0版本的发布，详情请参考：https://github.com/open-falcon/of-release/releases/tag/v0.1.0 。以下是新版本的主要内容：

API梳理和文档完善  OpenFalcon-team @hitripod
在新版本中，初步对Falcon已有的API做了整体的梳理，并对API文档进行了完善，具体可以参考http://docs.openfalcon.apiary.io ；在下个版本的规划中，会对OpenFalcon的API按照统一的标准和规范进行重新设计和开发，并将分散在各个模块中的API整合。

graph集群扩容时，历史数据自动迁移 OpenFalcon-team @yubo laiwei niean
graph集群扩容时，历史数据自动迁移，这是v0.1.0版本的最重要的feature之一，彻底解决了老版本graph扩容时会丢失一部分历史数据的问题。自动扩容操作指南 http://www.jianshu.com/p/16baba04c959

数据上报的最小间隔，可以在配置文件中更改 OpenFalcon-team @niean
在之前的版本中，OpenFalcon允许的最小数据上报间隔为30秒，如果要满足更小的上报间隔，那么需要用户修改transfer的代码并重新编译部署，比较麻烦。鉴于这个需求比较广泛，开发者社区在v0.1.0版本中对transfer进行了升级，允许通过修改配置来改变这个限制，不再需要修改代码了。

监控数据支持写入OpenTSDB 美团 OpenFalcon-team @Charlesdong
支持OpenTSDB，这是v0.1.0版本另一个最重要的feature，由OpenFalcon社区核心成员美团的同学们释出（OpenTSDB是一款基于Hbase的时间序列数据存储和展示系统，在全球范围内使用非常广泛，更多信息可以参考opentsdb.net ）OpenFalcon适配OpenTSDB，这样Falcon的用户，在使用Falcon强大的数据采集、告警功能的前提下，在数据展示、dashboard方面，有了更多的选择了。

适配支持grafana 快网 OpenFalcon-team @hitripod
适配grafana，同样是v0.1.0版本的一个最重要的feature，由OpenFalcon社区核心成员快网的同学们释出（grafana是一个全球范围内广泛使用的dashboard系统，支持Graphite, InfluxDB & OpenTSDB，更多信息参考grafana.org）现在同样支持OpenFalcon了。

详细指南，请参考 http://book.open-falcon.org/zh/dev/support_grafana.html

新增集群监控 OpenFalcon-team @ulricqin
集群监控，顾名思义，就是聚合某集群下的所有机器的一个或多个指标的值，提供一种集群视角的监控体验；这对于我们从集群的角度，整体来把握服务的状况非常有用。 该模块由OpenFalcon社区核心成员小米的同学们释出。 详细指南，请参考 http://book.open-falcon.org/zh/install_from_src/aggregator.html

新增nodata监控 OpenFalcon-team @niean
nodata，用于检测某些指标，在一段时间内由于异常原因没有上报的情况。该模块由OpenFalcon社区核心成员小米的同学们释出。 详细指南，请参考 http://book.open-falcon.org/zh/install_from_src/nodata.html

agent内置URL监控 @onlymellb
用户可以在portal中配置URL监控策略，agent会自动去检测相关的url是否健康。

agent支持对多个transfer的负载均衡 @cmgs
在agent中，可以配置多个transfer的地址，来达到负载均衡的目的；这对于不想使用LVS或者HAproxy的用户来讲会方便很多。

往HostGroup中添加机器的时候如果发现机器名不存在，就直接插入host表 @wkshare
这个问题，在上一个版本中，很多用户都有反馈，此次新版中对这块逻辑做了改进，对于那些指标中endpoint不是主机hostname的情况下，会方便许多。

dashboard绘图线条采用深颜色的配色方案 美团 OpenFalcon-team @skyeydemon
感谢美团的同学，上一张新配色方案的图


dashboard新的配色方案
下个版本(v0.2.0)的规划

统一整合dashboard、portal等前端模块
API按照统一的标准和规范进行重新设计和开发，并将分散在各个模块中的API整合
支持组合策略报警； 配置告警时，支持tag反选的功能
支持更灵活的索引查询能力
全站的权限控制统一化
历史告警信息存储和挖掘
发布时间，大约是在2016年的冬季

OpenFalcon沙龙

一个好消息，4月初，OpenFalcon社区联合麒麟会，组织一次小范围的沙龙，议题包括：

主题分享：量化一切——论服务监控体系
主题分享：美团、快网、小米等公司对于OpenFalcon的实践经验
主题分享：运维平台建设——CMDB&服务树&监控&部署
交友：网友大见面，相互学习，增进感情：）
此次沙龙，由于场地和预算有限，因此人数控制在100人左右，想参加的朋友，如果您不是OpenFalcon讨论组成员（请在OpenFalcon主页查看社区加入方式），请申请快快加入吧!

沙龙详细报名信息，会稍后放出，请关注OpenFalcon社区。

详细的changelog

请移步 http://book.open-falcon.org/zh/changelog/index.html
致谢

请移步 http://book.open-falcon.org/zh/contributing.html
License

Licensed under the Apache License, Version 2.0: http://www.apache.org/licenses/LICENSE-2.0
Copyright 2014-2015 Xiaomi, Inc.
Copyright 2016 open-falcon.org
