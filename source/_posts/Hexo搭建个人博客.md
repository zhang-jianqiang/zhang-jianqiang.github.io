---
title: Hexo搭建个人博客
date: 2023-02-28 12:43:38
tags:
typora-root-url: ..
---

## 环境准备

### git安装

git下载搜索官网即可

### node安装

node安装直接搜索官网即可

### 安装Hexo

```
$ npm install hexo -g
```

#### 安装hexo依赖

```
$ npm install --save hexo-deployer-git
```

## git配置ssh

### 生成`ssh key`

```
$ ssh-keygen -t rsa -C "你的邮箱"
```

复制用户目录下.ssh/id_rsa.pub下内容到github中添加ssh key

## 搭建个人博客

### 新建博客

```
# 初始化个人博客
$ hexo init
# 生成静态网页
$ hexo g
# 预览
$ hexo s
```

### 部署到github

github中新建一个仓库，仓库名使用`github用户.github.io`

<img src="/images/image-20230228125439693.png" alt="image-20230228125439693"  />

`git pages`设置

<img src="/images/image-20230228125647817.png" alt="image-20230228125647817" style="zoom:50%;" />

### 上传本地博客到github

![image-20231108221746463](/images/image-20231108221746463.png)

修改_config.yml

```yml
deploy:
  type: git
  repository: git@github.com:zhang-jianqiang/zhang-jianqiang.github.io.git
  branch: master
```

repository修改为自己的地址，bracnh修改为自己想要使用的分支

```
$ hexo d
```

此时访问`zhang-jianqiang.github.io`便能在线看到自己的博客
