---
title: 利用Cloudflare创建无限邮箱
date: 2024-01-05 15:15:47
tags:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202401051524426.webp
---

转自zhile大佬

[PandoraNext](https://github.com/pandora-next/deploy)是在老Pandora难以维护，以及GitHub号再三因为cocopilot被封，索性新起号新起的项目。

其实不是新东西了，很多朋友已经玩过很久了，仓库在这里：https://github.com/pandora-next/deploy

这次借着`v0.5.0`发布了一个好玩的功能，跟大家正式介绍一下。
一是为了说一说这个项目，第二点是为了介绍一下如何使用大善人`Cloudflare`的功能来配合`v0.5.0`的新功能。



对了，差点忘说`v0.5.0`发布了什么新功能，它就是**全代理ChatGPT账号注册流程**。
这意味着国内兄弟姐妹们注册**拥有一个自己的ChatGPT账号**难度降低`99%`。

##### 有人要问这跟自己去官网注册有何不同？我高低能给你凑出3条理由：

1. 免梯，这个懂的都懂，不多解释。
2. 不受ip注册数量限制，有时间你无限造。
3. 能装逼。（其实这一条就够了）

我简单测试了一下，`gmail`和`outlook`可以直接注册，而且`gmail`和`outlook`通过邮箱别名技巧可以多次注册。
国内邮箱`qq.com` `126.com` `163.com` 经测**不支持**。其他我还没试过，各位自行测试。

不过这些都不重要，我今天水这篇文章是为了告诉大家如何拥有无限邮箱，自己做大号商！现在开始：

#### 首先我们假设你已经有自己的域名，并且已经使用`Cloudflare`解析

###### 我是推荐用大善人Cloudflare的，白嫖点多多，你甚至还可以 [1分钟拥有热佬的网站](https://zhile.io/2023/09/04/copy-jetbra-in.html)。

1. 打开 [https://dash.cloudflare.com](https://dash.cloudflare.com/) ，找到你需要的域名。这里我使用我的`linux.do`举例。
   ![img](https://zhile.io/wp-content/uploads/2023/12/000.png)
2. 在左侧菜单中选择`Email` -> `Email Routing`（`电子邮件` -> `电子邮件路由`），如果你尚未启用，按照界面引导启用该功能即可。成功之后界面大概如下图（注意等路由状态为`已启用`方为生效）：
   ![img](https://zhile.io/wp-content/uploads/2023/12/1111.png)
3. 在`目标地址`选项卡中添加你希望转发到的邮箱地址（可以是QQ邮箱、126.com等国内邮箱），配置这个地址就是为了把只有所有`@linux.do`的邮件都转发到你这个地址，让你能进行注册验证等功能。
   ![img](https://zhile.io/wp-content/uploads/2023/12/222.png)
4. 添加目标地址如下图的例子（注意把邮箱换成你自己的），填写完成后这个地址显示`待验证`状态，同时`Cloudflare`会给你的这个邮箱发送一封验证邮件（验证所有权的意思，毕竟你不能随便用别人的邮箱不是）
   ![img](https://zhile.io/wp-content/uploads/2023/12/333.png)
   ![img](https://zhile.io/wp-content/uploads/2023/12/444.png)
5. 验证完成后回到`目标地址`选项卡后可以看到刚添加的邮箱地址是`已验证`状态。这些是接下来的前提操作。
   ![img](https://zhile.io/wp-content/uploads/2023/12/555.png)
6. 接下来点击`路由规则`选项卡，打开`Catch-All`的开关，并点击编辑按钮到达编辑界面。
   ![img](https://zhile.io/wp-content/uploads/2023/12/666.png)
7. 编辑界面选择如下图（注意替换成自己验证过的邮箱地址），然后保存即可。
   ![img](https://zhile.io/wp-content/uploads/2023/12/777.png)
8. 现在你拥有所有`xxx@linux.do`的邮箱地址了，我们来试一试注册一个ChatGPT账号看看。
   ![img](https://zhile.io/wp-content/uploads/2023/12/888.png)
9. 注册步骤开始，打开你部署的PandoraNext（如何部署不是文本讨论的话题，阅读仓库说明即可），也可到演示站： [https://chat.oaifree.com](https://chat.oaifree.com/) 登录界面点击 [Sign up](https://chat.oaifree.com/auth/signup) 链接。
   ![img](https://zhile.io/wp-content/uploads/2023/12/0000.png)
10. 输入你要注册的邮箱（可以用你刚才设置的邮箱，随便一个前缀，看图）和密码，点击`Continue`。
    ![img](https://zhile.io/wp-content/uploads/2023/12/11111.png)
11. OpenAI会给你发一封邮件，会由`Cloudflare`自动转发到你刚才设置的邮箱里收件（比如我设置的 `189650239@qq.com`），右键复制`Verify email address`（QQ邮箱可以点一下复制）的地址。
    ![img](https://zhile.io/wp-content/uploads/2023/12/33333.png)
    ![img](https://zhile.io/wp-content/uploads/2023/12/55555.png)
12. 把复制的验证链接（注意看链接开头应该如图所示）贴进注册界面的输入框，点`OK`按钮稍等片刻。
    ![img](https://zhile.io/wp-content/uploads/2023/12/22222-1.png)
    ![img](https://zhile.io/wp-content/uploads/2023/12/66666.png)
13. 在`Tell us about you`输入自己的名字（英文），点击`Continue`按钮，静静等待（可能会有验证码，按照界面指示验证即可）。
    ![img](https://zhile.io/wp-content/uploads/2023/12/77777.png)
14. 然后就成功了！
    ![img](https://zhile.io/wp-content/uploads/2023/12/88888.png)
15. 用刚才注册的号去登录吧，或者继续注册下去，下去，下去，下去。
    ![img](https://zhile.io/wp-content/uploads/2023/12/99999.png)
    ![img](https://zhile.io/wp-content/uploads/2023/12/101010.png)
16. 如果注册过程中出问题，比如说已经账号已存在之类的（此时可能是卡登录流程了）可以直接去登录试试，会恢复未完成的注册流程。**这是一条很重要的操作技巧**

#### 去造啊少年！不过请先去给项目 https://github.com/pandora-next/deploy 点个star吧～

### 反馈更新：

- 密码中不可包含用户名。
- 目前已知 `.cn`（包括`.com.cn`等） `.top` 域名后缀的注册是不被`OpenAI`支持的。
- 如果报错`the user already exists`，可能是由于以上不支持的原因造成。可直接登录试试，还是失败则可确定。
- 目前已知 `.com` `.org` `.net` `.io` `.do` `.fun` `.xyz` `.cc` `.me` `.cool` `.link` 后缀可注册。
