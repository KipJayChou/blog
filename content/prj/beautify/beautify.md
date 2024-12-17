---
title: "Hugo美化"
description: "Hugo Beautify"
date: '2024-12-09'
---


## Hugo美化网站

# Github-style

一个GitHub主题的Hugo主题：

参考网址：https://themes.gohugo.io/themes/github-style/

```bash
#获取主题：
git submodule add git@github.com:MeiK2333/github-style.git themes/github-style
#更新：
cd themes/github-style
git pull
#更改目录名
mv content/posts content/post
#设置README
hugo new readme.md
gedit content/readme.md
#修改ture为false

```

* 特色功能使用：

```bash
+++
......
pin = true
+++
#pin帖子
+++
......
summary = "The summary content"
+++
#显示摘要
enableGitalk = true

  [params.gitalk]
    clientID = "Your client ID"
    clientSecret = "Your client secret"
    repo = "repo"
    owner = "Your Github username"
    admin = "Your Github username"
    id = "location.pathname"
    labels = "gitalk"
    perPage = 30
    pagerDirection = "last"
    createIssueManually = true
    distractionFreeMode = false
#添加以上内容到config.toml,启动GitHub留言功能
[params]
  enableSearch = true

[outputs]
  home = ["html", "json"]

[outputFormats.json]
  mediaType = "application/json"
  baseName = "index"
  isPlainText = false
#添加以上内容到config.toml，实现本地搜索
```

![OLVF1j.png](https://ooo.0x0.ooo/2024/12/09/OLVF1j.png)

# Docsy

一个用于技术文档网站的 Hugo 主题：

参考网址：https://themes.gohugo.io/themes/docsy/



# Blowfish

Blowfish 是一个轻量有力的 Hugo 主题。它使用 Tailwind CSS 构建，洁净而富有极简主义，是你网站内容载体的不二之选。

参考网址：https://dgithub.xyz/nunocoracao/blowfish/blob/main/README.zh-cn.md

​		   https://blowfish.page/zh-cn/docs/getting-started/

 体验网址：https://blowfish.page/

* 确保已安装 **Node.js**、 **Git**、 **Go** 和 **Hugo** ，且已经创建了一个 Hugo 工程。✅

  1. 使用 npm（或其他软件包管理器）全局安装 CLI 工具：

  ```bash
  sudo cnpm i -g blowfish-tools
  #cnpm镜像下载
  ```

  2. 然后运行 "blowfish-tools "命令，开启一个交互式进程，引导你完成创建和配置。

  ```bash
  blowfish-tools
  ```

  ![OLVhHp.png](https://ooo.0x0.ooo/2024/12/09/OLVhHp.png)

* 配置 Blowfish 作为 git 子模块

  ```bash
  cd Hugo
  git submodule add -b main https://dgithub.xyz/nunocoracao/blowfish.git themes/blowfish
  #dgithub.xyz镜像下载
  #module很大，你忍一下（500MB+
  ```

* 在你的网站根目录中，删除 Hugo 自动生成的 `hugo.toml` 文件。从主题中复制 `*.toml` 文件，粘贴到 `config/_default/` 目录中。这将确保你的主题设置准确无误，在此基础上你能够轻松地自定义主题。

  ```bash
  cd themes/blowfish/_default
  gedit hugo.toml
  #确保内容有：
  theme = "blowfish" # UNCOMMENT THIS LINE（取消注释这一行
  baseURL = "https://kipjaychou.github.io/hugo/"
  defaultContentLanguage = "zh"
  ```

* 修改`languages.en.tom`l文件：

  ```bash
  mv languages.en.toml languages.zh.toml
  gedit languages.zh.toml
  #对部分修改内容，取消注释
  ```

* 修改`params.toml`文件：

  ```bash
  gedit params.toml
  #colorScheme 可选的值有blowfish （默认）、avocado、fire、ocean、forest、princess、neon、bloody、terminal、marvel、noir、autumn、congo和slate。
  ```

  部分颜色示例：

  ![OLVKcM.png](https://ooo.0x0.ooo/2024/12/10/OLVKcM.png)

* Hugo 默认是使用帖子、标签和类别，这三种可以开箱即用的。但如果你希望自定义，那么可以创建 `taxonomies.toml` 配置文件来实现：

  详细链接：https://gohugo.io/content-management/taxonomies/

  ```bash
  topic = "topics"
  ```

* **菜单**：

  Blowfish 有两个可以定制的菜单，以此来适配网站中的内容和布局。`main`菜单出现在网站头部，`footer`菜单出现在页面底部和版权声明上方。

  这两个菜单都是配置在 `menus.en.toml` 文件中。与语言配置文件类似，如果你希望使用另一种语言，请重命名这个文件并将 `en` 替换为你所希望的语言代码。

  ```bash
  mv menus.en.toml menus.zh.toml
  gedit menus.zh.toml
  ```

  ![OLVslC.png](https://ooo.0x0.ooo/2024/12/10/OLVslC.png)

  blowfish内置图标：https://blowfish.page/zh-cn/samples/icons/

  ```bash
  # 比如修改以下内容：
  [[main]]
    name = "Blog"
    pageRef = "posts"
    pre = "edit"
    weight = 10
  
  [[main]]
    name = "Github"
    pageRef = "https://github.com/KipJayChou"
    pre = "github"
    weight = 20
  ```

* **嵌套菜单**

  Blowfish 还支持嵌套菜单。你需要在`menu.toml` 中定义一个父级菜单项及其子菜单，使用 `parent` 可以指定子菜单项的父级。在上面菜单部分提到的所有参数一样适用于子菜单项，同样地，`pageRef` 和 `url` 也可以在父菜单项中使用。还需要注意一点，嵌套菜单只能在 `main` 菜单中可用，即网站头部的菜单。

  ```bash
  # config/_default/menus.toml
  
  [[main]]
    name = "Parent"
    weight = 20
  
  [[main]]
    name = "sub-menu 1"
    parent = "Parent"
    pageRef = "samples"
    weight = 20
  
  [[main]]
    name = "sub-menu 2"
    parent = "Parent"
    pageRef = "samples"
    weight = 20
  
  [[main]]
    name = "sub-menu 3"
    parent = "Parent"
    pre = "github"
    pageRef = "samples"
    weight = 20
  
  ```

  

* **子导航菜单**

  此外，你可以设置一个子导航菜单。只需要在 `menus.toml` 中将新的菜单项定义为 `subnavigation` 即可。 这将在主菜单下面展示第二行，其中包含子类别项。

  ```bash
  # config/_default/menus.toml
  
  [[subnavigation]]
    name = "An interesting topic"
    pageRef = "tags/interesting-topic"
    weight = 10
  
  [[subnavigation]]
    name = "My Awesome Category"
    pageRef = "categories/awesome"
    weight = 20
  
  ```

* **缩略图 & 背景**

  Blowfish 的创立开端旨在便于为文章添加视觉效果。如果你熟悉 Hugo 的文章结构，只需要在你文章所在的文件夹中，放置一个以`feature*`开头的图像文件（Blowfish支持所有格式的文件，但更推荐使用 `.png` 或 `.jpg`）。就这样，Blowfish 就能够将图像文件作为文章的缩略图，而且能够在社交平台的 `<a target="_blank" href="https://oembed.com/">oEmbed</a>` 卡片中使用。

# 抓bug：

1. ## 使用了`dgithub.xyz`导致403

   要换成`github.com`

   更新子模块 URL 并同步和更新子模块不会重置你对 Blowfish 主题的配置文件。子模块的更新只会影响子模块的代码，而不会影响你项目中的配置文件。

   ### 具体步骤

   1. **更新子模块 URL**：

      ```bash
      git submodule set-url themes/blowfish https://github.com/nunocoracao/blowfish.git
      ```

   2. **同步子模块**：

      ```bash
      git submodule sync --recursive
      ```

   3. **更新子模块**：

      ```bash
      git submodule update --init --recursive
      ```

   #### 解释

   - **`git submodule set-url`**：
     - 这个命令只会更新子模块的 URL，不会影响你的项目文件或配置。

   - **`git submodule sync --recursive`**：
     - 这个命令会将子模块的 URL 更新到 `.git/config` 文件中，确保 Git 使用新的 URL 进行克隆。它不会影响你的项目文件或配置。

   - **`git submodule update --init --recursive`**：
     - 这个命令会初始化并更新子模块，确保子模块的代码是最新的。它只会更新子模块的代码，不会影响你的项目文件或配置。

   #### 总结

   更新子模块 URL 并同步和更新子模块不会重置你对 Blowfish 主题的配置文件。子模块的更新只会影响子模块的代码，而不会影响你项目中的配置文件。你可以放心地更新子模块，而不用担心配置文件被重置。

2. ## GitHub pages找不到hugo.toml

   由于`blowfish`文档说要删除/Hugo根目录下的`hugo.toml`，而且`GitHub pages`找不到在`~/Hugo/themes/blowfish/config/_default`的`hugo.toml`,于是：

   ```bash
   touch hugo.toml
   gedit hugo.toml
   #内容如下：
   baseURL = "https://kipjaychou.github.io/Hugo/"
   languageCode = "en-us"
   title = "My Hugo Site"
   theme = "blowfish"
   
   [params]
     contentDir = "content"
     sectionPagesMenu = "main"
   ```

   

3. ## Hugo install.md的date格式不符合 YAML 规范

   ```bash
   #错误：
   ---
   date = '2024-12-08'
   draft = false
   title = 'Hugo Install'
   ---
   #正确：
   ---
   date: '2024-12-08'
   draft: false
   title: 'Hugo Install'
   ---
   ```







```markdown
---
title: "自部署"
description: "自部署笔记教程"
---

### docker
### Uptime-Kuma
### FnOS
### Hugo
### Nginx
```

安装
