---
date: '2024-12-09'
draft: false
title: 'Hugo配置'
thumbnail: "/home/parallels/Pictures/Test/content/projects/hugo-config/featured.png"
---


## 配置HUGO

* 参考文献：https://gohugo.io/getting-started/quick-start/

1. 验证hugo版本 > v0.128.0

2. 运行这些命令以使用 Ananke 主题创建 Hugo 站点:

   ```bash
   hugo new site Hugo
   #创建您的项目目录结构在 quickstart 目录中
   cd Hugo
   git init
   #初始化当前目录下的空 Git 仓库。
   git submodule add https://dgithub.xyz/theNewDynamic/gohugo-theme-ananke.git themes/ananke
   #将 Ananke 主题克隆到 themes 目录中，将其作为 Git 子模块添加到您的项目中。
   #将一个 Git 仓库作为子模块（submodule）添加到当前的 Git 仓库中。
   echo "theme = 'ananke'" >> hugo.toml
   #向网站配置文件中添加一行，指明当前主题。
   hugo server
   #启动 Hugo 的开发服务器以查看网站。
   ```

   可以在localhost:1313访问初始网页

#### 创建内容：

```bash
hugo new content content/posts/hugo-install.md
```

在md文本内加入内容：[✅Hugo1.0安装.md](file:///Users/jay/Desktop/%E8%87%AA%E9%83%A8%E7%BD%B2%E6%9C%8D%E5%8A%A1%E7%AC%94%E8%AE%B0/%E2%9C%85Hugo1.0%E5%AE%89%E8%A3%85.md)

保存文件，然后启动 Hugo 的开发服务器以查看网站。您可以使用以下任一命令包含草稿内容.

```bash
hugo server --buildDrafts
hugo server -D
```

当您对新的内容满意时，将前言的 `draft` 参数设置为 `false` 。

![OLdxUi.png](https://ooo.0x0.ooo/2024/12/08/OLdxUi.png)

成功显示内容！

#### 配置网站

* 在Hugo目录下，修改内容为以下：

  ```bash
  nano hugo.toml
  #填入以下内容
  baseURL = 'https://kipjaychou.org/'
  languageCode = 'zh-cn'
  title = 'KipJayChou HOME'
  theme = 'ananke'
  ```

  

* 启动 Hugo 开发服务器以查看您的更改，记得包括草稿内容。

  ```bash
  hugo server -D
  hugo server --buildDrafts
  ```

  ![OLdzvX.png](https://ooo.0x0.ooo/2024/12/08/OLdzvX.png)

#### 发布网站

* 在这个步骤中，您将发布您的网站，但不会部署它。

* 当你发布你的网站时，Hugo 会在你的项目根目录下的 `public` 目录中创建整个静态网站。这包括 HTML 文件以及图像、CSS 文件和 JavaScript 文件等资源。

* 当你发布网站时，通常不希望包含草稿、未来或过期的内容。命令很简单。

  ```bash
  hugo
  ```
