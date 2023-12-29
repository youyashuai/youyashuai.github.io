---
title: PAC提取http(https)代理地址
date: 2023-12-29 17:27:12
tags:
top_img: 
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312291731890.png
---

原理：pac文件是javascript函数，通过插件Proxy switchy 可查看修改后的编码段；

若加密，则可通过开发者工具，在控制台Console中键入decodeURI()反编译解密真实http(s) proxy

![图片alt](https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312291731130.png "图片title")