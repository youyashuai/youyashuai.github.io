---
title: Gemini-proxy利用Cloudflare搭建
date: 2024-01-04 17:00:52
tags:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202401041708682.png
---

转自zhile大佬

谷歌新一代AI：Gemini发布有一段日子了，**免费1分钟能调用60次**，很慷慨了。
谷歌不像某些班子（你知道我说的是谁），其实没什么限制。就在我以为大家都能顺顺利利用上它的时候，却经常能在群里看到群友说自己访问不了、梯子某个节点无法访问Gemini。
听到这些，我知道我水文章的机会来了：跟大家说说怎么更好地白嫖Gemini。



今天继续用我们的大善人cloudflare（简称cf）来达成我们的目的。如果你看过我[之前的文章](https://zhile.io/2023/12/09/pandoranext-introduction.html)，你应该已经有个域名在cf了。那就跟着文章的步骤开始吧。

首先打开 [https://dash.cloudflare.com](https://dash.cloudflare.com/) 在左侧菜单点击`Workers 和 Pages`

![img](https://zhile.io/wp-content/uploads/2023/12/111.png)

点击`创建应用程序`按钮

![img](https://zhile.io/wp-content/uploads/2023/12/222-1.png)

点击`创建Worker`按钮

![img](https://zhile.io/wp-content/uploads/2023/12/333-1.png)

给你的worker起个名字，我们这里就叫`gemini-pro-proxy`吧，不重要。然后点击`部署`按钮即可。

![img](https://zhile.io/wp-content/uploads/2023/12/444-1.png)

你会看到一个部署成功的页面。页面中包含一个域名，这是你worker的默认域名。如果你自己没有域名，之后你可以直接用这个域名，但应该需要梯子（对梯子质量要求不高）。我们到这一步直接点击`编辑代码`按钮。

![img](https://zhile.io/wp-content/uploads/2023/12/555-1.png)

在出来的代码编辑页面，填入以下几行代码：

```js
export default {
  async fetch(request, env) {
    const url = new URL(request.url);
    url.host = 'generativelanguage.googleapis.com';
    return fetch(new Request(url, request))
  }
}
```

JavaScript

Copy

点击右上角的`保存并部署`按钮即可。

![img](https://zhile.io/wp-content/uploads/2023/12/666-1.png)

点击左上角你worker的名字，这里是`gemini-pro-proxy`就可以看到你部署worker的详细信息。

完成以上步骤，其实你的gemini代理就已经就绪了。你已经可以直接使用你worker的默认地址来替换gemini的api地址，不会再有谷歌阻止你访问。

![img](https://zhile.io/wp-content/uploads/2023/12/777-1.png)

但如我所说，此时你还是需要梯子去访问你的worker地址，因为gfw默认封禁了这个域名后缀。

接下来我们进一步设置，用自己的域名去访问。

转到自己在cf上域名的控制面板，点击左侧菜单`DNS`来添加域名解析。
这里我使用自己的域名`baipiao.io`，给它增加了子域名A记录：`gemini.baipiao.io`

![img](https://zhile.io/wp-content/uploads/2023/12/888-1.png)

这里有两个要点：

1. 不要开启小黄云。
2. ip地址可以使用cf的优选工具选出来的高质量ip。

我这里用了两个我觉得还不错的ip，你们可以直接用，也可以自己去优选。

DNS解析记录操作完毕之后，点击左侧菜单`Workers路由`来让我们设置的域名和worker的路由关系。
在`Workers路由`界面，点击`添加路由`按钮，参考如下填写：

![img](https://zhile.io/wp-content/uploads/2023/12/999.png)

这里域名换成你刚才设置的那个，Worker也选择你之前创建的。点击`保存`即可。

完成这一步你就可以用你自己的域名来请求gemini了。比如我这个域名：

Gemini官方给的例子是：

```bash
curl \
  -H 'Content-Type: application/json' \
  -d '{"contents":[{"parts":[{"text":"Write a story about a magic backpack"}]}]}' \
  -X POST https://generativelanguage.googleapis.com/v1beta/models/gemini-pro:generateContent?key=YOUR_API_KEY
```

Bash

Copy

我们替换`generativelanguage.googleapis.com`部分到我们的域名`gemini.baipiao.io`

```bash
curl \
  -H 'Content-Type: application/json' \
  -d '{"contents":[{"parts":[{"text":"Write a story about a magic backpack"}]}]}' \
  -X POST https://gemini.baipiao.io/v1beta/models/gemini-pro:generateContent?key=YOUR_API_KEY
```

Bash

Copy

对了，附一下Gemini Pro的api key获取地址：https://makersuite.google.com/app/apikey

和沉浸式翻译的Gemini设置：

![img](https://zhile.io/wp-content/uploads/2023/12/0000-1.png)

### 总结步骤

1. 添加一个cf的worker，代理gemini的api地址。
2. 优选ip，设置自己的域名解析（防墙、提速）。
3. 绑定自己的域名和worker。
4. 你要是实在不会弄，你就用我搭的那个吧。

