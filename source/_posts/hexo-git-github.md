---
title: hexo搭建属于自己的博客
date: 2022-02-01 21:13:10
tags: hexo git github
---

准备阶段
====
----------
首先包管理器用于导入hexo所需要的包，可去官网自行**下载nodejs**，然后**下载git包管理器**（将项目文件上传至github、gitee（远程仓库永久管理项目）或者是从github、gitee拉取项目至本地）。git帮助将本地已经写好的静态博客网页上传至远程仓库管理，之后可以通过https://githubname.github.io仓库名称直接访问。另外需要github账号和git账号 

初期
==
----------
github的前期工作
-----------
首先在github建一个名为github账号名.github.io的仓库，然后SSH获取，与本地连接，
 `git config --global user.name "yourname"
git config --global user.email "youremail"`
输入github用户名和邮箱用于git确认，
然后
`git config user.name git config user.email` 查看上输入是否正确
创建SSH `ssh-keygen -t rsa -C "youremail"`
取到电脑用户文件下找到.ssh文件夹下的id_rsa.cup公钥 另外一个id_rsa是私钥，再到github仓库去新建ssh密钥

hexo搭建工作
--------
----------
本地新建一个文件夹命名存放hexo项目，右击git bash 在命令行输入`hexo init <folder>`进行框架初始化搭建，可以新建文章`hexo new [布局文件] "文章标题" //布局文件默认使用 config.yml 中的 default_layout 参数代替` 也可以新建页面`hexo new page "title" 
参数: 
    -p : 指定页面路径,如-p about/me
    -r 如果存在同名文章替换
    -s 作为文章发布后的文件名和url`
也可以后期加，`hexo generate 或者 hexo g` 自动生成public文件夹，修改_config.yml文件，拉到最后，
`deploy:
  type: 'git'
  repo: git@github.com:h-sina/h-sina.github.io.git
  branch: main`

连接Hexo与Github
-------------

`hexo server` 启动服务器,可以在本地直接看到效果，`hexo deploy `部署网站 简写 `hexo d`，等于将本地的静态文件上传至github仓库，然后直接gihubusername.gihub.io之前建的那个仓库名就能访问到hexo搭建的博客。

> *小结：简单的部署了解具体流程，页面还未按照自己的喜好搭建，主要是hexo的配置，然后git和github的连接，ssh这些问题。*