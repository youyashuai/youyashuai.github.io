---
title: GeminiPro项目部署方法
date: 2024-01-04 10:28:58
tags:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202401041442095.webp
---
合理使用GeminiPro API项目
开源项目地址https://github.com/Deeptrain-Community/chatnio
![](https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202401041442095.webp)
支持线上部署 [Vercel](https://vercel.com/new/clone?repository-url=https://github.com/babaohuang/GeminiProChat&env=GEMINI_API_KEY&envDescription=Google%20API%20Key%20for%20GeminiProChat&envLink=https://makersuite.google.com/app/apikey&project-name=gemini-pro-chat&repository-name=gemini-pro-chat&demo-title=Gemini%20Pro%20Chat&demo-description=Minimal%20web%20UI%20for%20Gemini%20Pro.&demo-url=https%3A%2F%2Fgeminiprochat.com&demo-image=https%3A%2F%2Fgeminiprochat.com%2Ficon.svg)  、[Railway](https://railway.app/template/v9QL5u?referralCode=tSzmIe)、 [Zeabur](https://zeabur.com/templates/1103PJ)
Docker部署使用命令行
```bash
docker run --name geminiprochat \
--restart always \
-p 3000:3000 \
-itd \
-e GEMINI_API_KEY=your_api_key_here \
babaohuang/geminiprochat:latest
```
请确保将 your_api_key_here 替换为你自己的 Gemini API 密钥。
这将启动 geminiprochat 服务，访问地址为 “http://localhost:3000”
环境变量

| 名称                | 说明                                                         | 必填  |
| ------------------- | ------------------------------------------------------------ | ----- |
| `GEMINI_API_KEY`    | 你的 Gemini API 密钥。可以从[此处](https://makersuite.google.com/app/apikey) 获取。 | **✔** |
| `API_BASE_URL`      | Gemini API 的自定义基本 URL。点击[此处](https://github.com/babaohuang/GeminiProChat/README_cn.md#solution-for-user-location-is-not-supported-for-the-api-use)查看何时使用这个。 | ❌     |
| `HEAD_SCRIPTS`      | 在页面的“”之前注入分析或其他脚本                             | ❌     |
| `PUBLIC_SECRET_KEY` | 项目的密文字符串。用于为 API 调用生成签名                    | ❌     |
| `SITE_PASSWORD`     | 为网站设置密码，支持用逗号分隔的多个密码。如果不设置，网站将允许公开访问 | ❌     |

本地部署

环境

1. **Node**: 检查你的开发环境和部署环境是否都在使用 `Node v18` 或更高版本。你可以使用 [nvm](https://github.com/nvm-sh/nvm) 在本地管理多个 `node` 版本。

   ```bash
    node -v
   ```

2. **PNPM**: 我们建议使用 [pnpm](https://pnpm.io/) 来管理依赖关系。如果从未安装过 pnpm，可以使用以下命令进行安装：

   ```bash
    npm i -g pnpm
   ```

3. **GEMINI_API_KEY**: 在运行此应用程序之前，你需要从 Google 获取 API 密钥。你可以前往 https://makersuite.google.com/app/apikey，申请 API 密钥。

 部署

1. 安装依赖

   ```bash
    pnpm install
   ```

2. 复制 `.env.example` 文件并重命名为 `.env`，并在 `.env` 文件中添加 [`GEMINI_API_KEY`](https://makersuite.google.com/app/apikey)。

   ```bash
    GEMINI_API_KEY=AIzaSy...
   ```

3. 运行应用程序，项目会在 `http://localhost:3000/` 上运行。

   ```bash
    pnpm run dev
   ```

Error解答

#### 关于 API 使用过程中 “User location is not supported for the API use” 的解决方案

如果你遇到了 **“User location is not supported for the API use”** 的问题，请按照以下步骤进行解决：

1. 前往 [**palm-netlify-proxy**](https://github.com/antergone/palm-netlify-proxy) 仓库并点击其中的 **“Deploy With Netlify**。
2. 部署完成后，你将收到 Netlify 分配的域名 （例如 `https://xxx.netlify.app`）。
3. 在你的 **Gemini Pro Chat** 项目中，设置名为 `API_BASE_URL` 的环境变量，其值为部署 palm-proxy 时获得的域名 (`https://xxx.netlify.app`)。
4. 重新部署你的 **Gemini Pro Chat** 项目来完成配置。这应该可以解决问题。
