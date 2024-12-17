---
date: '2024-12-09'
draft: false
title: 'Hugo安装'
---

> 1. Create a site
> 2. Add content
> 3. Configure the site
> 4. Publish the site

我将在parallels desktop提供的Debian虚拟机上演示从安装配置到成型的过程：

* 安装HUGO

  安装hugo（扩展版或扩展/部署版，v0.128.0 或更高版本）

  官网：https://gohugo.io/installation/linux/

  要安装HUGO，必须先安装git，go，dart sass：

  * git：
    - Build Hugo from source
      从源代码构建 Hugo
    - Use the [Hugo Modules](https://gohugo.io/hugo-modules/) feature
      使用 Hugo 模块功能
    - Install a theme as a Git submodule
      安装主题作为 Git 子模块
    - Access [commit information](https://gohugo.io/methods/page/gitinfo/) from a local Git repository
      从本地 Git 仓库访问提交信息
    - Host your site with services such as [CloudCannon](https://cloudcannon.com/), [Cloudflare Pages](https://pages.cloudflare.com/), [GitHub Pages](https://pages.github.com/), [GitLab Pages](https://docs.gitlab.com/ee/user/project/pages/), and [Netlify](https://www.netlify.com/)
      托管您的网站，使用 CloudCannon、Cloudflare Pages、GitHub Pages、GitLab Pages 和 Netlify 等服务
  * go：
    - Build Hugo from source
      从源代码构建 Hugo
    - Use the Hugo Modules feature
      使用 Hugo 模块功能
  * Dart Sass：
    * Dart Sass is required to transpile Sass to CSS when using the latest features of the Sass language.
      Dart Sass 是使用 Sass 语言的最新功能时将 Sass 转换为 CSS 所必需的。

  #### 安装hugo的方法：

  1. 预构建的二进制文件

     ```bash
     git clone https://dgithub.xyz/gohugoio/hugo.git
     ```

     Download---extract---move---add PATH---chmod

  2. 使用包管理器

     * snap安装

     ```bash
     sudo apt-get install snapd
     #先安装snap
     sudo snap install hugo
     #安装hugo扩展版
     sudo snap connect hugo:removable-media
     #启用对可移动媒体访问权限
     sudo snap connect hugo:ssh-keys
     #要启用对 SSH 密钥的访问：
     ```

     * homebrew安装

     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     #安装homebrew（macos和linux的包管理器）
     sudo brew install hugo
     #brew安装hugo
     ```

     

  3. 代码仓库包安装

     debian apt安装

     ```bash
     sudo apt install hugo
     ```

  4. 从源代码构建：

     > Git
     >
     > GO （version：1.20+）
     >
     > GCC / Clang
     >
     > add PATH

     ```bash
     CGO_ENABLED=1 go install -tags extended,withdeploy github.com/gohugoio/hugo@latest
     ```

     自主学习GO：https://go.dev/doc/code#Command

     * 完整地安装配置GO：

       ```bash
       #安装go
       sudo apt-get update
       sudo apt-get install golang-go
       go version
       #配置go
       export GOPATH=$HOME/go
       export PATH=$PATH:$GOPATH/bin
       source ~/.bashrc
       （source ~/.zshrc）
       echo $GOPATH
       echo $PATH
       ```

     * 添加 Hugo 到 `PATH`

       ```bash
       export PATH=$PATH:$GOPATH/bin
       source ~/.bashrc  # 如果你使用的是 bash
       source ~/.zshrc   # 如果你使用的是 zsh
       echo $PATH
       ```

