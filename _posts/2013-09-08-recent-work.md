---
layout: post
title: 最近的工作
description: 最近一直在构思这篇博客的内容，到现在还是不知道从何下手。自从将博客从wordpress迁移到github上之后，就很少在博客写一些关于工作和生活的文章，所以想写一篇关于工作的博客，记录最近做过的事情以及一些当时的所思所想。 
category: work
tags: [work]
---

最近一直在构思这篇博客的内容，到现在还是不知道从何下手。自从将博客从wordpress迁移到github上之后，就很少在博客写一些关于工作和生活的文章，所以想写一篇关于工作的博客，记录最近做过的事情以及一些当时的所思所想。

最近半年多一直在做hadoop方面的工作，也就是接触hadoop才半年多时间。最开始接触hadoop是去年的11月21日，那天去Intel公司参加了两天的hadoop培训。培训的内容很多干货也有很多枯燥的东西，所以边听边瞌睡的听完了两天的培训内容。培训的ppt打印出来了，时不时地会翻看上面讲述的内容，然后在网上搜索些相关的资料。

最先接触的hadoop发行版是Intel的IDH，刚开始使用IDH也就是用他的管理界面安装、部署hadoop集群，然后在8节点的集群上作hive两表关联的测试。测试结果不是很满意，但是对IDH倒是印象深刻。IDH的前端使用GWT开发，界面简洁，操作也比较方便，只是同步配置文件有时候非常慢，要等上一杯咖啡的时间。

<!-- more -->

IDH的源代码不开源，所以遇到一些问题的时候，只能先自己摸索。我不喜欢闭源也不喜欢许可证以及混淆代码什么的。虽然java代码的混淆了，但是shell和puppet脚本还是能够很容易读懂的。参考IDH的部署安装脚本，我在试着用shell编写一个hadoop的安装部署脚本，这个工作还在慢慢进行中。也许在弄懂puppet的原理和代码之后，我会简化、改进IDH的脚本；也许会使用公司使用的saltstack来完善这个部署脚本。

IDH实现了hive over hbase，这是一个很不错的特性，其基于hbase的协作器，代码实现并不复杂。IDH中有个hmon用于监控hadoop，我已经把这部分代码反编译了。

在hadoop版本选择的过程中，体验了Cloudera的CDH。首先是CDH的压缩包手动安装hadoop集群，一点点的修改配置文件，直到最后集群能够成功启动，这种方式安装的hadoop集群不包含本地lib文件；然后又试着解压缩Cloudera-manager.bin文件，尝试在虚拟机中不连接网络的情况下通过Cloudera-manager来安装配置集群，在使用了一段时间之后，发现Cloudera-manager没有使用操作系统的service服务来管理hadoop组件的启动和停止，而是有自己一套实现来管理集群，再加上Cloudera-manager也不开源，故放弃了使用Cloudera-manager来安装集群的方式；最后，最后是使用rpm方式来安装hadoop，安装过程倒是不复杂，只是以后如果自己修改了源代码时候升级不是很方便了，Cloudera的github上有个cdh-package项目，这个其实就是apache的bigtop项目，试过通过这个来编译出hadoop的rpm包，没有成功。

IDH通过本地文件来保存集群的配置信息，而CDH将这些信息保存到数据库了。CDH的Cloudera-manager的web界面基于bootstrap和jquery插件，ui做的很不错，通过反编译java代码，已经知道了其web界面的实现方式以及编译成功了部分java代码。CDH的Cloudera-manager和IDH-manager也很大不同，我想在这两个的基础上也实现一个hadoop的manager，这是我个人想法，还需要研究、整理出他们的实现思路，然后一点点的构思自己该怎么做。Cloudera-manager免费版简称CMF。

差不多两个月前，公司想做个hive的查询界面，这个东西其实就是和hwi、hue差不多的个东西。基于Spring，我很快搭好了框架，然后把CMF其中的css和js都迁移过来了。这是我第一次接触bootstrap，稍微修改下代码一个前台框架就弄好了，CMF最主要是使用了require.js使javascript代码模块化，这东西改起来也很简单，我把CMF中大部分基础javascript代码都移到了我搭好的框架中。搭好这个框架没花多少时间，但后来公司不打算使用这一套框架，以后有时间我会继续基于这个框架开发个hadoop的管理界面。

在使用ganglia监控hadoop的过程中，有时候需要找一个监控指标需要花好长时间，而且一个页面上显示的指标太多的时候，这个页面会反应不过来。hortonworks的HDP发行版中似乎对ganglia做了些修改，具体不知道改了什么。HDP发行版没有使用和研究过，只是下载了1.3和2.0两个版本的VM，然后看了看其中的hue，觉得做的很不错，只可惜是python写的。

在使用hadoop的过程中，觉得hadoop的门槛对于用户来说还是有点高。用户需要学习hive语法，写出的sql语句通常都不是最优sql，如果有个sql优化器自动帮用户优化sql语句就好了。hbase用于监控业务日志，数据建模和编写代码查询数据对于业务人员来说难度也太大了，如果能够适度封装，让业务人员不用关心hadoop的细节，只需要编写sql语句就能查询数据该多好啊！

其他工作：hive和mapreduce调优。

上面是最近在做的一些事情，包括暂停没做的、正在做的以及还未做的。有时候觉得有些事情很简单，但没有时间、没有精力也没有自由一下子做完，有些时候人在江湖，身不由己。







