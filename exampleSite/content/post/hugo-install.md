---
title: 从零开始 Hugo 建站教程
author: "世佳"
date: 2020-09-02
keywords: Hugo 视由 视界事由 eyecus 博客 blog Markdown 
description: Hugo是由Go语言实现的静态网站生成器，简单、易用、高效、易扩展、快速部署。

isCJKLanguage: true
weight: 1

type: post

categories:
- Web

tags: 
- Blog
- Web
- Html
- Hugo
- Markdown
---

`Hugo`是由Go语言实现的静态网站生成器，简单、易用、高效、易扩展、快速部署,本站即为 Hugo 博客框架搭建。

<div align="center"> 
<img src="https://cdn.jsdelivr.net/gh/eyecus/cdn/img/hugo.svg" width=300 />
</div>

> **相关站点**：
    <a href="https://gohugo.io" target="_blank">Hugo官网</a>
    <a href="https://themes.gohugo.io" target="_blank">Hugo主题</a>
    <a href="https://www.gohugo.org" target="_blank">Hugo中文</a>
    <a href="https://github.com/gohugoio/hugo" target="_blank">Hugo仓库</a>


## 第1步 安装Hugo框架

首先根据自己的系统参照下述方法进行安装。

### macOS

macOS操作系统下直接使用 [Homebrew](https://brew.sh) 安装，在终端中输入如下代码：
```   
brew install hugo
```

在终端输入如下命令安装 `Homebrew`。
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
国内用户如果下载缓慢或安装失败，可使用国内加速源下载。
```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

### Windows
在 [Hugo Releases](https://github.com/gohugoio/hugo/releases) 下载最新发布对应操作系统的`ZIP`，将所有内容提取到`C:\Hugo\bin`目录中，包含可执行文件`hugo.exe`、`LICENSE`和`README.md`。然后将Hugo添加到Windows的`PATH`设置中。

1. 右键单击「开始」按钮
1. 单击「系统」
1. 单击左侧的「高级系统设置」
1. 单击底部的「环境变量...」按钮
1. 在「用户变量」部分中找到以PATH开头的行（PATH全部大写）
1. 双击「PATH」
1. 单击「新建…」按钮
1. 键入`C:\Hugo\bin`，完成输入后按「回车」
1. 在每个窗口中单击「确定」退出

### Linux
Linux操作系统下直接使用[ Homebrew ](https://brew.sh)安装，在终端中输入如下代码:
```   
brew install hugo
```

在终端输入如下命令安装 `Homebrew`。
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```
国内用户如果下载缓慢或安装失败，可使用国内加速源下载。
```
/bin/zsh -c "$(curl -fsSL https://gitee.com/cunkai/HomebrewCN/raw/master/Homebrew.sh)"
```

### OpenBSD
OpenBSD通过`pkg_add`添加Hugo的软件包：
```   
doas pkg_add hugo
```


### 源码安装
执行源码安装前请确保安装有 [ Git ](https://git-scm.com/)、[ Mercurial ](https://www.mercurial-scm.org/)、[ Go ](http://golang.org/)。在 [Hugo Releases](https://github.com/gohugoio/hugo/releases)下载对应操作系统的Hugo安装文件，执行安装。


设置好`GOPATH`环境变量，获取源码(源码会下载到`GOPATH/src`目录)并编译。
```
export GOPATH=$HOME/go
go get -v github.com/spf13/hugo
```

安装完Hugo后，在终端中输入如下代码验证安装。

```
hugo version
```

## 第2步 生成网站

在终端中输入如下代码生成网页。代码中`test`是所创建的网站文件夹名称，由用户自定义，以下网站名均由`test`代指。
```
hugo new site test
```

## 第3步 网站配置(套用主题)

进入网站根目录

```
cd test
```

安装`Git`（用于下载主题及安装）

```
git init
```

在主题商店中选择自己喜欢的主题，查看其` Github `仓库地址，使用如下代码克隆主题至本地。代码中网址为主题Github仓库地址，`XXXX`为主题文件夹名称。

Hugo 主题商店地址: <a href="https://themes.gohugo.io/" target="_blank">Hugo 官方主题商店</a>、<a href="https://www.gohugo.org/theme/" target="_blank">Hugo 中文主题商店</a>。

```
git clone https://github.com/XXXXX/XXXX themes/XXXX
```

编辑网站根目录中`config.toml`文件，添加代码`theme = "XXXX"`以确认所使用的主题。`config.toml`文件默认格式如下：
```
baseURL = "https://example.org/"
languageCode = "en-us"
title = "test"
theme = "XXXX"
```

## 第4步 添加页面

添加新页面，页面内容采用 [Markdown](/web/markdown/) 格式。

```
hugo new posts/my-first-post.md
```
页面默认格式如下，代码中`my-first-post`为Markdown页面文件名，`title: "My First Post"`所写内容才是网站显示的标题，页面格式根据主题不同略有不同，详见主题描述。
```
---
title: "My First Post"
date: 2019-10-20T00:00:00+01:00
draft: true
---
```

## 第5步 运行网站

完成上述操作后，可在终端中输入如下代码运行网站。浏览器访问 [http://localhost:1313](http://localhost:1313/) 预览效果。你可在预览的同时对网站进行编辑，网页将会实时展示修改后的效果，如果出现刷新问题可通过`Ctrl+R`进行强制刷新。
```
hugo server -D
```

## 第6步 生成静态网页

在终端中输入如下代码生成静态网页。这个命令并不会生成草稿页面，需要生成的页面请去掉页面头部的`draft: true`。

默认情况下生成的文件会输出到`test/public/`目录下，你可将改文件夹部署到服务器以实现远程访问，也可使用本文第7步所说的方法。
```
hugo
```


## 第7步 部署 Github Pages

执行此操作前请确保拥有Github账号，并创建一个以`XXX.github.io`命名的空仓库，其中`XXX`为你的Github用户名。在终端中输入如下代码生成最终页面。
```
hugo --theme=XXXX --baseUrl="http://XXX.github.io/"
```

在终端中输入下列代码将最终页面部署到 Github Pages。
```
cd public
git init
git remote add origin https://github.com/XXX/XXX.github.io.git
git add -A
git commit -m "first commit"
git push -u origin master
```

浏览器输入` http://XXX.github.io `实现远程访问。除本文使用的 Github Pages 外，你还可以使用 Coding 和 Gitee 等。
