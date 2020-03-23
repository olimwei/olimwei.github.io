---
layout: post
title: 用jekyll和github把网站建起来！
categories: 科技, 学习
tags: jekyll, github, git, 网站
---
先把这些天学习的用jekyll在github上搭建网站的步骤记录下来，留作参考。

#安装jekyll

确定系统安装 Git, Ruby, RubyGems, Nodejs, Python2.7. 如何安装，狗狗一搜就可以。mac上基本自带，注意update一下到最新版本。

```
$ gem install jekyll bundler
$ jekyll -v # 检查安装帮版本
$ jekyll new my-awesome-site
$ cd my-awesome-site
$ jekyll serve
# => Now browse to http://localhost:4000
```

通过jekyll serve -B启动服务，使用Rakefile创建文章，然后用自己喜欢的工具进行写作。

创作完成，通过jekyll build生成页面，本地localhost:4000查看文章。

#注册github账户

注意创建第一个仓库用 username.github.io 在用户名下再创建的仓库可类似于网站下的一个folder. 

# SSH 配置

```
在用户目录（比如：C:/User/www）新建 .ssh 文件夹，或者通过 mkdir .ssh 创建。
cd .ssh，并执行 ssh-keygen -t rsa -C "your_email@example.com"。
连续三次回车，可以不用输入内容。第一次是指写入的文件名，默认为 id_rsa，后两次为密码。
将 .pub 后缀文件中的内容复制出来，登陆 GitHub，找到页顶的设置项，然后设置其中的 ssh 项，添加刚才复制的内容。
```

# 两种方式在github上搭建网站

- 在本地建好网站，上传到github
- 从github上clone一个到本地，修改完传回

# 1. 本地创建

``` 
$ mkdir my-site
$ cd my-site
$ git init # 初始建立本地git仓库
$ git remote add origin git@github.com:username/username.github.io.git # 建立和远端仓库链接
$ git pull # 最好先提取一下，不然可能会有问题
$ echo "hello world" >> README.md # 创建第一个readme文件。或用其它方式在本地仓库创建网站内容。
$ git add . # 把新增或改动加入缓冲
$ git commit -m "first commit" # 提交到本地仓库
$ git push -u origin master # 推送到远端， 这里是github网上仓库
```

# 2. 从远端克隆

``` 
$ git clone https://github.com/username/username.github.com.git
# 这个方法把远端仓库拷贝到本地，并建立一个username.github.com的目录。
$ cd username.github.com
# 在本地完成一些修改后创建新的网页或博客文章
$ git add . # 把新增或改动加入缓冲
$ git commit -m "revision" # 提交到本地仓库
$ git push -u origin master # 推送到远端， 这里是github网上仓库
```

新手可以找个喜欢的网站fork一下，再克隆到本地，修改之后传回github. 如直接克隆别人的网站，一定要记得要重新设定远端，设成自己的github仓库。

# 域名绑定

github上设置很简单，记得分支选master. 也可以自己添加CNAME文件。(别人那里克隆来的，记得修改成自己的域名）。

二级域名在域名注册商那里修改A记录为：204.232.175.78 # 这可能会变，google找最新可用的IP地址

三级域名或子域名可用CNAME设置。 如 www 指向 username.github.io 或 username.github.io/another-rep


# 一些git命令

```
git init // 当前项目 git 化  
git add . // 当前目录加入 git 跟踪  
git add filename // 当前文件 filename 参加 git 跟踪  
git commit -m "XXXX" // 提交信息，交给 git 经管，提交到本地库  
git remote add origin git@github.com:XXXX/YYYY.git // 与 GitHub 上项目链接 (ssh 方式)  
git push -u origin master // 将本地库提交到 GitHub 上，另一种是 gh-pages  
git rm -rf directory // 删除库中指定文件夹 directory 所有内容  
git rm filename // 删除库中指定文件 filename 内容   
git clone git＠github.com:XXXX/YYYY.git // 将 GitHub 上的项目下载下来 
git pull // 把服务器上的 “拉” 下来，与本地的合并
```

# [这里是git简明指南](http://rogerdudler.github.io/git-guide/index.zh.html)

![git cheat sheet](http://byte.kde.org/~zrusin/git/git-cheat-sheet-large.png)

# [这里是jekyll的一些模版](http://jekyllthemes.org)

# [这里是jekyll tips网站](http://jekyll.tips)

[Jekyll Now repository](https://github.com/barryclark/jekyll-now) on GitHub.
