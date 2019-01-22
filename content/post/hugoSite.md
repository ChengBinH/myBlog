---
title: "使用Github，Hugo创建属于自己的个人博客"
date: 2019-01-22T16:08:17+08:00
lastmod: 2019-01-22T16:08:17+08:00
toc: false # 关闭文章目录
draft: false # 关闭草稿
comment: false # 关闭评论
mathjax: true # 打开 mathjax
tags: ["博客"] # 标签
categories: ["Hugo","site"] # 分类
author: "Cheng" # 作者
---

# <center>(本教程的运行环境为Ubuntu18.04)<center/>

# 背景

### &emsp;&emsp;其实在大三暑假开始就想搭建一个个人的静态博客，网上查询了很多的资料，发现很多人都是利用Github搭建，于是想使用Github搭建一个免费的个人博客,但是发现使用的模板有多种，于是就放弃了,到了开学居然很快的就搭起来了。想想其实上学期寒假也是，想在Ubuntu进行编程，但是笔记本安装了四五次一直识别不了U盘，就放弃了，到了开学莫名其妙就可以了，之后就一直在Ubuntu进行开发。


### &emsp;&emsp;我搭建博客使用的是Github+Hugo。Hugo是一个用 Go 语言编写的静态网站生成器,就我个人使用而言，安装Hugo不需要太多的依赖，使用起来较方便。

# Ubuntu下安装Hugo

- 使用命令行安装
```
    sudo apt-get install hugo
```
- 图形化安装

    - 在Ubuntu软件中搜索hugo，并安装

- 验证hugo是否安装
```
    // 命令行输入
    hugo version

    // 输出与以下类似即可
    Hugo Static Site Generator v0.47.1 linux/amd64 BuildDate: 2018-08-24T17:11:12Z
```

# 创建第一个博客

```
// 1. 在自己想要生成网站的路径打开终端

// 2. 生成hugo模板网站
hugo new site myBlog

// 3. 创建的模板目录说明

|- archetypes ：存放default.md，头文件格式

|- content ：content目录存放博客文章（.markdown/.md文件）

|- data ：存放自定义模版，导入的toml文件（或json，yaml）

|- layouts ：layouts目录存放的是网站的模板文件

|- static ：static目录存放js/css/img等静态资源

|- public : public目录存放生成的网站，这里的文件push到github上就可以使用网络访问

|- themes : theme目录是存放下载的主题

|- config.toml ：config.toml是网站的配置文件

作者：_风流倜傥
链接：https://www.jianshu.com/p/f1b02e00f206
來源：简书
```

# 快速使用主题

- 下载主题
    
    - 这里需要使用到github,如未配置请看Ubuntu下的Git以及Github配置

```
    cd myBlog

    // 这里我使用到的时jane主题
    // 地址为：https://github.com/xianmin/hugo-theme-jane，可以自行看中文说明

    // 下载主题
    git clone https://github.com/xianmin/hugo-theme-jane.git --depth=1 themes/jane
```

- 复制网站配置信息

```
    cp themes/jane/exampleSite/config.toml ./

    // 回到上级
    cd .. 

    // 复制默认的文章模板页
    cp themes/jane/archetypes/default.md archetypes/
```

- 启动hugo server：

``` 
    hugo server
```
打开 http://localhost:1313/ ，你将会看到一个示例网站。

- 创建自己第一篇文章

```
    hugo new post/first.md
```

# 开始你的博客

- 默认配置文件 config.toml 位于你的网站的根目录，请按自身需要进行定制。

- 默认的文章文件位于 ./content/post 目录。

- 其他可以看该主题的中文说明

# 生成网站

- 直接运行 hugo ，将会自动生成你的网站到 public/ 目录。

# 保存到github
- 在github创建一个 yourname.github.io的repository

- 上传public下的文件到github（ssh方式）

```
1-git init                 # 本地仓库初始化，执行完后会在工程目录下生成一个.git的隐藏目录

2-git add .               # 添加所有文件到本地索引，命令用法：git add <file>

3-git commit -m "My first commit"   # 提交修改到本地仓库，-m选项添加提交注释

4-git remote add origin git@github.com:yourname/yourrepositoryname.git   # 添加远程仓库地址，保存在origin变量中

5-git push origin master      # 按照前一条命令中origin给定的github地址推送到github仓库的master分支
```
# 后续更新
            可以使用vs code进行编码，后需提交文章只需要使用 hugo server 实时预览效果，使用 hugo 命令更新文章，然后把public下的文章push到github上就可以了

# 访问网站
```
https://yourname.github.io
```
# 配置自己的域名
            使用github提供的域名毕竟没有自己的域名好用，所以一般都会到域名提供商哪里购买域名。这个我就不说明了。国内可以到万网购买域名，然后使用cloudflare免费给域名提供ssl和cdn加速，提高网站的安全性和访问速度。

