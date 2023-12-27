---
title: Hexo+Github+Vercel搭建个人博客网站实录
date: 2023-12-27 17:16:39
tags:
  - Hexo
  - 主题
  - 教程
  - Butterfly
  - Github
  - Git
categories:
  - 教程
  - Hexo
keywords: "Hexo,教程,Butterfly,Git,Github,npm"
description:
top_img:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312272212421.webp
---

在利用[Hexo](https://so.csdn.net/so/search?q=Hexo&spm=1001.2101.3001.7020)+Github Pages写我们的博客的时候，真正的原始Hexo文件在我们的电脑本地，而GitHub上传的只是Hexo生成的静态网页，即public文件夹里面的内容。

那么假如我们有两台电脑工作，Hexo最开始搭建在其中一台电脑上，而我们需要在另外一台电脑上同时更新我们的博客，该怎么做呢？

也就是说，我们需要实现多台电脑间博客项目的迁移与同步。为实现这一点，我们可以利用Git的分支。

## 创建分支

博客搭建好后(博客搭建教程见——[利用Hexo框架从零开始搭建个人博客我们在[Github](https://so.csdn.net/so/search?q=Github&spm=1001.2101.3001.7020)上创建分支


创建一个名为hexo的分支

## 设置hexo分支为默认分支

https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312272212421.webp



![图片alt](https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312272212421.webp "图片title")

## 

将博客项目仓库的Settings->Branches->Default branch修改为hexo
![hexo](https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312272212421.webp)
