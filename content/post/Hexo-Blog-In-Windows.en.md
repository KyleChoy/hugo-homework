---
title: "Built Free Blog Website Using Hexo And Github Under Windows"
date: 2020-04-13T22:25:03+08:00

categories: ["Website"]
tags: ["Hexo", "Github", "Blog"]
author: "Kyle"
---
This article comes from my blog website：[https://kylechoy.github.io](https://kylechoy.github.io/Windows-%E4%B8%8B%E4%BD%BF%E7%94%A8-Github-%E6%90%AD%E5%BB%BA%E5%85%8D%E8%B4%B9%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2.html)
<!--more-->
### Ⅰ、Install Softwar
#### 1. [Node.js](https://nodejs.org/en/download/)
If in China you can also visit [淘宝 Node.js 镜像](https://npm.taobao.org/mirrors/node) .
#### 2. [Git](https://git-scm.com/download/win)
If in China you can also [从蓝奏云下载](https://ww.lanzous.com/b00zedhte)
#### 3. Hexo
Creat a new directory as the workplace of your blog website, right-click your mouse at the blank space of File Manager, press `Git Bash Here` , then type:
```bash
npm install -g hexo-cli
```
Then:
```bash
hexo init Blog
```
The name `Blog` can be replaced by any words.
```bash
cd Blog         #Goto workplace
npm install
```
Then your workplace will look like this:

```bash
├── _config.yml      #Config File
├── package.json     #Applications's Config
├── scaffolds        #Template
├── source           #User's Resources
|   ├── _drafts      #Drafts
|   └── _posts       #Posted Articles
└── themes           #Themes
```
Then:
```bash
hexo init
hexo s      #s stands for start
```
Now use your browser to visit `http://localhost:4000` and you'll see it!

### Ⅱ、Deploy Hexo to GitHub Pages
#### 1. Creat Repository
Visit [Github.com](https://github.com/) , after logging in:
* `New Repositorie`
* Write `xxx.github.io` in `Repository name`
* Choose `Creat Respository`
  
Note: xxx can be customized, but not for **.github.io**


#### 2. Generate SSH Key and Add it to GitHub
* Go back to Git Bash, type:
```bash
git config --global user.name "yourname"
git config --global user.email "your@emial.com"
```
Input your Github username and mail address.

* Generate SSH Key:
```bash
ssh-keygen -t rsa -C "your@email.com"
```
Then edit `id_rsa.pub` , copy whatever in it.

Add to Github：
`Github -> Avatar -> Settings -> SSH and GPG keys -> New SSH Key`, paste it.


#### 3. Deploy Hexo to Github
* Install deploy-git:
```bash
npm install hexo-deployer-git --save
```
* Edit Config:
  
open `_config.yml` , modify the last few lines:
```bash
deploy:
  type: git
  repo: git@github.com:UserName/name.github.io.git
  branch: master
```
Replace the link after `repo` as `Github -> YourRespository -> Clone or Download -> Use SSH`, example:

![](https://i.loli.net/2020/04/20/YeBSHcVouyMtxKl.png)

* Deploy
```bash
hexo clean
hexo generate
hexo deploy
```
`generate` and `deploy` can be replaced by `g` and `d` .


#### 4. Check Your Website
Wait for a second and you can visit your website at `xxx.github.io`

***
References:

[Hexo Docs](https://hexo.io/docs/index.html)

[Hexo史上最全搭建教程](https://blog.csdn.net/sinat_37781304/article/details/82729029)