---
title: 使用Fiddler抓取HttpClient的包
date: 2017年10月24日18:39:59
tags: 
-  排序
categories:
- java
---

### 使用Fiddler抓取HttpClient的包
>  使用Fiddler，默认是无法抓取HttpClient的包，需要在程序中设置一下。  

HttpHost proxy = new HttpHost("localhost",8888);
RequestConfig=config=RequestConfig.custom().setProxy(proxy).setConnectTimeout(10000).setSocketTimeout(15000).build();
CloseableHttpClient httpClient=HttpClientBuilder.create().setDefaultRequestConfig(config).build();