---
title: "Windows 下使用 Hexo 和 Github 搭建免费个人博客"
date: 2020-04-13T22:25:03+08:00

categories: ["网站"]
tags: ["Hexo", "Github", "Blog"]
author: "Kyle"
---
此篇文章来自我的又双叒叕一个博客网站：[https://kylechoy.github.io](https://kylechoy.github.io/Windows-%E4%B8%8B%E4%BD%BF%E7%94%A8-Github-%E6%90%AD%E5%BB%BA%E5%85%8D%E8%B4%B9%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2.html)
### Hexo 简介
Hexo 是一款基于 Node.js 的快速、简洁且高效的博客框架，依赖少易于安装使用，可以方便的生成静态网页托管在 GitHub 上，支持 Markdown。
<!--more-->
### 一、安装相关软件
#### 1. [Node.js](https://nodejs.org/en/download/)
若访问缓慢可以前往 [淘宝 Node.js 镜像](https://npm.taobao.org/mirrors/node) 下载
#### 2. [Git](https://git-scm.com/download/win)
若遇到下载问题可以 [从蓝奏云下载](https://ww.lanzous.com/b00zedhte)
#### 3. Hexo
新建一个文件夹作为博客的目录，在文件管理器空白处 `右键` - `Git Bash Here` ，输入以下命令：
```bash
npm install -g hexo-cli
```
安装完成后对 Hexo 进行初始化：
```bash
hexo init Blog
```
这个 `Blog` 可以替换为任意名字，将会生成对应的文件夹。
```bash
cd Blog         #进入生成的目录
npm install
```
新建完成后，指定文件夹的目录如下：

```bash
├── _config.yml      #网站配置信息
├── package.json     #应用程序的信息
├── scaffolds        #模版文件夹
├── source           #用户资源文件夹
|   ├── _drafts      #草稿文章
|   └── _posts       #已发布文章
└── themes           #主题
```
之后输入：
```bash
hexo init
hexo s      #s是start的缩写，输入start也可以
```
此时用浏览器打开 `http://localhost:4000`，就可以看到你的网站啦！

### 二、将 Hexo 部署到 GitHub Pages
#### 1. 创建个人仓库
进入 [Github.com](https://github.com/) ，登录后选择：
* `New Repositorie（新建仓库）`
* `Repository name` 填入 `xxx.github.io` 
* 选择 `Creat Respository`
  
注意：xxx可以换为其他字符，但是 **.github.io** 不能更改


#### 2. 生成 SSH 密钥并添加到GitHub
* 返回 Git Bash，输入：
```bash
git config --global user.name "yourname"
git config --global user.email "your@emial.com"
```
输入自己在 Github 的用户名（**区分大小写**）和邮箱

* 创建 SSH 密钥： 
```bash
ssh-keygen -t rsa -C "your@email.com"
```
完成后会提示生成文件的位置，以文本的方式打开 `id_rsa.pub` ，复制里面所有内容。
* 把密钥添加到 Github：
进入 `Github -> 点击头像-> Settings -> SSH and GPG keys`
点击 `New SSH Key`，把复制的内容全部粘贴进去


#### 3. 将 Hexo 部署到GitHub
* 安装 deploy-git
```bash
npm install hexo-deployer-git --save
```
* 修改站点配置文件
  
打开网站根目录下 `_config.yml` ，修改最后的内容：
```bash
deploy:
  type: git
  repo: git@github.com:UserName/name.github.io.git
  branch: master
```
其中，`repo` 后的链接替换为：`Github -> 仓库页面 -> Clone or Download -> Use SSH -> 文本框内容`，如下图：

![SSH](/hugo/img/SSH.png)

* 部署
```bash
hexo clean
hexo generate
hexo deploy
```
其中 `generate` 和 `deploy` 可以用 `g` 和 `d` 代替


#### 4. 查看网站
稍等片刻后，浏览器进入`xxx.github.io`就可以看到自己的网站了。
（xxx为之前自己创建时填入的名字）


***
参考资料：

[Hexo官方文档](https://hexo.io/zh-cn/docs/index.html)

[Hexo史上最全搭建教程](https://blog.csdn.net/sinat_37781304/article/details/82729029)