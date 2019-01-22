---
title: "Linux常用命令"
date: 2019-01-22T16:28:53+08:00
lastmod: 2019-01-22T16:28:53+08:00
toc: false # 关闭文章目录
draft: false # 关闭草稿
comment: false # 关闭评论
mathjax: true # 打开 mathjax
tags: ["cmd"] # 标签
categories: ["Linux","cmd"] # 分类
author: "Cheng" # 作者
---

# linux 学习，命令行备忘
1. ssh远程服务器

    - ssh -p (port 默认22 可省略) root@ip

    - ssh-keygen -R ip 清除ssh的登录信息

2. 拷贝文件

    - scp -P (port 默认22 可省略) 文件 服务器用户名@ip:远程服务器路径 (本地拷贝文件到远程服务器)

    - scp -P (port 默认22 可省略) 服务器用户名@ip:远程服务器文件 本地路径 (远程服务器拷贝文件到本地)

3. 端口、进程

    - netstat -ntlp 查看端口占用

    - kill -9 pid 杀进程

    - ps aux | grep pid 根据pid查看进程

    - top、gotop 查看计算机内存、处理器等信息


4. 软件更新,卸载

- Ubuntu
1. apt-get

    - sudo apt-get update 更新源

    - sudo apt-get upgrade 检查更新软件
    - sudo apt-get install 软件名 安装软件
    - sudo apt-get remove (–purge 可选) 卸载软件 清除配置
    - sudo apt-get autoremove
    - sudo apt-get clean
    - sudo apt-get autoclean
2. dpkg

    - dpkg -i xxx.deb 安装deb软件包

    - dpkg -r xxx.deb 删除软件包
    - dpkg -r –purge xxx.deb 连同配置文件一起删除
    - dpkg -info xxx.deb 查看软件包信息
    - dpkg -L xxx.deb 查看文件拷贝详情
    - dpkg -l 查看系统中已安装软件包信息

5. 查看文件

    - tail 倒序查看

    - head 正序查看

    - cat 查看文件所有内容

6. 防火墙

    - sudo ufw status 查看防火墙状态以及开放的端口

    - sudo ufw enable/disable 开/关防火墙

    - sudo ufw allow 端口号 开放端口

    - sudo ufw delete allow 端口号 删除端口

    - sudo ufw allow from ip 开放ip

    - sudo ufw delete allow from ip 删除ip

7. nohup 在后台运行

    - nohup commond > /dev/null 2>&1 & 后台且输出进程号

8.  java

    - java -jar -Dspring.profiles.active=dev xxx.jar 开发环境

9. mysql

    - 导入sql文件 mysql -u 用户名 -p 数据库名 <.sql文件位置

    - 导出sql文件
```
mysqldump -u用户名 -p密码 数据库名 > blod_$(date +%Y%m%d_%H%M%S).sql
```
10. 修改时间

    - sudo tzselect 选择地区

    - sudo cp /usr/share/zoneInfo/Asia/Shanghai /etc/localtime 复制新的时间文件

    - sudo ntptime time.windows.com 更新时间

11.   配置文件

```

    # jdk配置

    sudo vim /etc/profile

    #set Java environment

    export JAVA_HOME=/jdkhome

    export JRE_HOME=$JAVA_HOME/jre

    export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH

    export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH

    source /etc/profile

    # manven 配置

    建立Maven的HOME目录变量：

    export M2_HOME=/home/gzx/apache-maven-3.3.9

    将Maven的bin目录添加到path路径

    PATH=$M2_HOME/bin:$PATH

    source /etc/profile
```