---
title: Pandora-next获取ChatGpt token
date: 2024-01-05 17:06:52
tags:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202401161718848.webp
---

项目地址：[https://github.com/pandora-next/deploy](https://bulianglin.com/g/aHR0cHM6Ly9naXRodWIuY29tL3BhbmRvcmEtbmV4dC9kZXBsb3k)
项目文档：[https://fakeopen.org/PandoraNext](https://bulianglin.com/g/aHR0cHM6Ly9mYWtlb3Blbi5vcmcvUGFuZG9yYU5leHQ)
官方获取Access Token和Session Token：[https://chat.openai.com/api/auth/session](https://bulianglin.com/g/aHR0cHM6Ly9jaGF0Lm9wZW5haS5jb20vYXBpL2F1dGgvc2Vzc2lvbg)
获取Access Token和Session Token：[https://ai.fakeopen.com/auth](https://bulianglin.com/g/aHR0cHM6Ly9haS5mYWtlb3Blbi5jb20vYXV0aA)
生成Share Token：[https://ai.fakeopen.com/token](https://bulianglin.com/g/aHR0cHM6Ly9haS5mYWtlb3Blbi5jb20vdG9rZW4)
生成Pool Token：[https://ai.fakeopen.com/pool](https://bulianglin.com/g/aHR0cHM6Ly9haS5mYWtlb3Blbi5jb20vcG9vbA)
第三方WebUI：[https://github.com/Yidadaa/ChatGPT-Next-Web](https://bulianglin.com/g/aHR0cHM6Ly9naXRodWIuY29tL1lpZGFkYWEvQ2hhdEdQVC1OZXh0LVdlYg)

## 使用Web模式

免费账号共享池：[https://baipiao.io/chatgpt](https://bulianglin.com/g/aHR0cHM6Ly9iYWlwaWFvLmlvL2NoYXRncHQ)
官方演示地址一：[https://chat.oaifree.com](https://bulianglin.com/g/aHR0cHM6Ly9jaGF0Lm9haWZyZWUuY29t)
官方演示地址二：[https://chat1.zhile.io](https://bulianglin.com/g/aHR0cHM6Ly9jaGF0MS56aGlsZS5pbw)
别人搭建的网址：[https://fofa.info/result?qbase64=Ym9keT0iQ29udGludWUgd2l0aCBBY2Nlc3MgVG9rZW4iICYmIHRpdGxlPSJQYW5kb3JhTmV4dCIgJiYgY291bnRyeT0iQ04i](https://bulianglin.com/g/aHR0cHM6Ly9mb2ZhLmluZm8vcmVzdWx0P3FiYXNlNjQ9WW05a2VUMGlRMjl1ZEdsdWRXVWdkMmwwYUNCQlkyTmxjM01nVkc5clpXNGlJQ1ltSUhScGRHeGxQU0pRWVc1a2IzSmhUbVY0ZENJZ0ppWWdZMjkxYm5SeWVUMGlRMDRp)

反向代理Pandora：[https://cloudflare.com](https://bulianglin.com/g/aHR0cHM6Ly9jbG91ZGZsYXJlLmNvbQ)
[RProxy.zip](https://bulianglin.com/usr/uploads/2023/12/2305427416.zip)

```javascript
export default {
  async fetch(request, env) {
    let url = new URL(request.url);
    url.hostname = 'chat.zhile.io'
    return fetch(new Request(url, request));
  },
};
```

## 使用Proxy模式（自己搭建）

license_id（根据github账号年限获取使用额度）：[https://dash.pandoranext.com](https://bulianglin.com/g/aHR0cHM6Ly9kYXNoLnBhbmRvcmFuZXh0LmNvbQ)

```bash
#下载pandora
https://github.com/pandora-next/deploy/releases
#后台运行pandora
nohup ./PandoraNext > pandora.log 2>&1 &

#下载pandora-get-token.py
https://raw.githubusercontent.com/bulianglin/demo/main/pandora-get-token.py
#后台运行载pandora-get-token.py
nohup python3 -u pandora-get-token.py > gettoken.log 2>&1 &
```

**Bash**

共享Pool Token：`pk-this-is-a-real-free-pool-token-for-everyone`
