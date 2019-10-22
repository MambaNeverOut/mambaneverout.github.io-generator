---
title: "如何用hugo搭建个人博客"
date: 2019-10-22T14:47:50+08:00
draft: false
---

## 大家好啊，第一篇博客就来介绍一下如何用hugo搭建一个简单的个人博客。

1. 安装Hugo,下载链接：https://github.com/gohugoio/hugo/releases。   
   ```
   hugo version
   ```
  下载完成后可以通过下面的指令检测是否下载成功。  

2. 建立新网站 
   ```
   hugo new site blog
   ```
  上面的代码将在名为的文件夹中创建一个新的Hugo网站blog。

3. 添加主题(默认主题为Ananke主题)
   ```
   cd blog

   git init

   git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

   echo 'theme = "ananke"' >> config.toml
   ```

4. 创建新的博客
   ```
   hugo new post/开博.md
   ```
   可以编辑新创建的文件内容，它将从以下内容开始：
   ```
   ---
   title: "开博"
   date: 2019-10-22T08:47:11+01:00
   draft: true
   ---
   ```
  注意：draft 是指草稿的意思，默认是true（不显示），写完博客记得修改为false，然后才会在你的博客中显示。

5. 启动Hugo服务器
   ```
   hugo server -D
   ```
  默认在 http://localhost:1313 中显示。
   
  