---
title: Hexo在多台电脑设备同步提交更新github_pages博客
date: 2023-12-28 22:06:22
tags:
top_img:
cover: https://cdn.jsdelivr.net/gh/youyashuai/pic@main/img/202312282306157.webp
---

本文采用主流解决方案：创建git分支实现多设备Hexo项目的同步与更新
#### 创建分支
创建名为hexo的分支（名字随意）
#### 设置hexo分支为默认分支
项目仓库的Settings->Branches->Default branch修改为hexo
#### 克隆远程hexo分支仓库到本地
```bash
git clone https://github.com/xxx.github.io.git
```
#### 删除hexo分支除.git之外的内容
删除克隆本地的hexo分支文件夹除.git之外的内容
执行bash命令更新删除到远程
```bash
git add -A
git commit -m "--"
git push origin hexo
```
将hexo分支克隆到本地的.git文件夹复制到Blog文件夹
#### 将修改后的文件夹推送远程hexo分支
在Blog文件夹下执行bash命令
```bash
git add -A
git commit -m "提交描述"
git push origin hexo
```
Tips ：注意themes目录下如存在.git需要删除，嵌套git会无法上传主题
#### 在其他电脑设备克隆hexo分支
安装git、node.js、npm环境
```bash
git clone https://github.com/xxx.github.io.git
```
进入克隆本地项目文件夹，安装依赖，生成静态文件
```bash
npm install
hexo g
hexo s
```
本地预览网站http://localhost:4000
发布博文执行hexo三连
```bash
hexo clean && hexo g && hexo d
```
#### 分支hexo中网站原始文件同步更新
执行bash命令
```bash
git pull
git add -A
git commit -m "描述"
git push origin hexo
```
#### 在每台设备上同步更新 
```bash
git pull 或 git pull hexo
```
