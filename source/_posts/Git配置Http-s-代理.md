---
title: Git配置Http(s)代理
date: 2023-12-29 17:44:52
tags:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312291750638.webp
---

在某些情况下需要添加Git代理，公司仅提供pac代理文件，主要作用于网络层中的应用层，对Git难以奏效

pac文件为js文件，可进行反编译来获得Git所需的http(s)代理，[PAC提取http(https)代理地址](https://www.vercel.cloudns.org/2023/12/29/PAC%E6%8F%90%E5%8F%96http(s)%E4%BB%A3%E7%90%86%E5%9C%B0%E5%9D%80/)

##### 添加Git 代理

Bash环境下，输入以下命令：

```
git config --global http.proxy "http://agent.xxxx.com:8888"
git config --global https.proxy "https://agent.xxxx.com:8888"
```

Tips：http://agent.xxxx.com:8888 替换为自己的proxy

##### 删除Git 代理

```
git config --global --unset http.proxy
git config --global --unset https.proxy
```

##### 查看Git 代理状态

```
git config --global --get https.proxy
```
