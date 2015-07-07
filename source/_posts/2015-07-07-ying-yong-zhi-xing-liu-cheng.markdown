---
layout: post
title: "应用执行流程"
date: 2015-07-07 23:02:16 +0800
comments: true
categories: 
---

1、\fitetl\src\com\fitech\model\etl\service\hsyh\ExportData.java
![image](/images/20150612/1.png)
程序入口，ETLConductExportService处理主要内容。


2、\fitetl\src\com\fitech\model\etl\service\hsyh\ETLConductExportService.java
![image](/images/20150612/2.png)
主要功能在方法writerUploadFile中实现，由于采用oracle数据库，调用createRptFile生成报文。


3、\fitetl\src\com\fitech\model\etl\service\hsyh\FitechRpt\service\impl\RptOprServiceImpl.java
![image](/images/20150612/3.png)
全部报文，调用方法creRptFileAll

![image](/images/20150612/4.png)
调用方法creRpfFileSgl

![image](/images/20150612/5.png)
![image](/images/20150612/6.png)
![image](/images/20150612/7.png)
![image](/images/20150612/8.png)
每10000行创建一个新的线程，线程RptExpOprThread用来生成报文。


4、\fitech\model\etl\service\hsyh\FitechRpt\util\RptExpOprThread.java
![image](/images/20150612/9.png)
调用方法createSplitRpt


5、\fitetl\src\com\fitech\model\etl\service\hsyh\FitechRpt\util\RptUtil.java
![image](/images/20150612/10.png)
调用方法createRptFile

![image](/images/20150612/11.png)
![image](/images/20150612/12.png)
生成报文文件