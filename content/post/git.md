---
title: "Ubuntu下Github配置"
date: 2019-01-22T16:02:34+08:00
lastmod: 2019-01-22T16:02:34+08:00
toc: false # 关闭文章目录
draft: false # 关闭草稿
comment: false # 关闭评论
mathjax: true # 打开 mathjax
tags: ["git"] # 标签
categories: ["Ubuntu","git"] # 分类
author: "Cheng" # 作者
---

# 安装Git

- 添加Git的PPA源
```
    sudo add-apt-repository ppa:git-core/ppa
```
- 更新PPA源的软件
```
    sudo apt-get update // 更新源的软件版本
    sudo apt-get upgrade // 更新本地软件版本
```
- 安装Git
```
    sudo apt-get install git
```
- 测试Git是否安装完成
```
    git version // 如果显示版本号就表示安装成功
```
# Github配置（以下配置在终端中配置）

- 配置Github用户名和邮箱
```
    git config --global user.name "github用户名"

    git config --global user.email "github邮箱"

    git config --list // 查看github配置
```
- 配置ssh公钥
```
    ssh-keygen -t rsa -C "github邮箱" 

    // 输入该命令后，一直回车即可
    // 该命令完成后会在 当前用户目录 ~/.ssh/下生成密钥文件 

    cat /home/yourusername/.ssh/id_rsa.pub 

    // 获取公钥 
    // 把终端显示的内容拷贝
    // 登录Github，
    // 找到Settings里的SSH and GPG keys
    // 点击New SSH key
    // Title 随意填，把上面拷贝的公钥粘贴到Key
    // 点击Add SSH key 保存公钥
```

- 验证Github是否配置成功
```
    ssh -T git@github.com

    // 如果显示如下就成功了
    // Hi yourname! You've successfully authenticated, but GitHub does not provide shell access.
```

# Github额外的操作
##  git设置代理（以下前提为Ubuntu配置了Shadowsocks-qt5，并成功连上）
- git config –global https.proxy http://127.0.0.1:1080

- git config –global https.proxy https://127.0.0.1:1080

- git config –global http.proxy ‘socks5://127.0.0.1:1080’

- git config –global https.proxy ‘socks5://127.0.0.1:1080’

## 取消代理(配置代理的前提下进行操作)
- git config –global –unset http.proxy

- git config –global –unset https.proxy

