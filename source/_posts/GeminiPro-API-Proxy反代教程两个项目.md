---
title: GeminiPro API Proxy反代教程项目部署
date: 2024-01-04 10:30:09
tags:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202401041712330.png
---
Gemini-Proxy项目
1、palm-proxy
项目地址：https://github.com/antergone/palm-proxy
线上部署： [vercel](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fantergone%2Fpalm-proxy)

教程 <u>[https://simonmy.com/posts/使用vercel反向代理google-palm-api.html](https://simonmy.com/posts/使用vercel反向代理google-palm-api.html)</u>

[https://simonmy.com/posts/使用netlify反向代理google-palm-api.html](https://simonmy.com/posts/使用netlify反向代理google-palm-api.html)

2、gemini-proxy

项目地址：

线上部署：[vercel](https://vercel.com/new/clone?repository-url=https://github.com/CaoYunzhou/gemini-proxy)

官方使用示例

```
curl https://generativelanguage.googleapis.com/v1beta/models?key=$API_KEY
```

Vercel反代后的使用示例

```
curl https://gemini.aivvm.com/v1beta/models?key=$API_KEY
```

```
curl https://gemini.aivvm.com/v1beta/models/gemini-pro:generateContent?key=$API_KEY \
    -H 'Content-Type: application/json' \
    -X POST \
    -d '{
      "contents": [
        {"role":"user",
         "parts":[{
           "text": "鲁迅为什么打周树人？"}]},
      ]
    }'
```

 沉浸式翻译配置如下

- API KEY 填Google的秘钥
- 自定义 API 接口地址：

```
 https://gemini.aivvm.com/v1/models/gemini-pro:generateContent?key={key}
```