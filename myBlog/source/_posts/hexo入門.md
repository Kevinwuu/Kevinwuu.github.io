---
title: "[Hexo架站懶人包] - 入門"
date: 2022-06-04
categories: 前端
tags: hexo
---


## What’s hexo

一種靜態網站產生器。

讓你可以用工程師最常用的md檔案產生網頁，建立自己的部落格

除了發布內容外，也有非常豐富的背景主題還實用套件讓開發者直接套用

如留言系統、訪客人數、RSS等

<!--more-->

## How to use

當你想要建立自己的部落格和網站時，總不可能只想給自己一個人孤芳自賞看辛酸的

因此怎麼選擇網域和部署方式絕對是分不開的問題

個人目前使用的方案是Github page搭配Netlify部署

### Installation

dependencies

- Nodejs
- hexo
- Git

```bash
npm install -g hexo-cli

// 確定是否正確啟動
hexo -v
```

```bash
hexo init <project_name>  //初始化新的 Hexo，會在當前路徑建立 project_name的資料夾

cd <project_name>
npm install

```

### 專案結構

```bash
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes

```

### 

- scaffolds
鷹架資料夾。當您建立新文章時，Hexo 會根據 scaffold 來建立檔案。
- source
原始檔案資料夾是放置內容的地方。
    
    檔案 / 資料夾名稱開頭為 _ (底線) 和隱藏檔案會被忽略，除了 _posts 資料夾以外。Markdown 和 HTML 檔案會被處理並放到 public 資料夾，而其他檔案會被拷貝過去。
    
- themes
主題 資料夾。Hexo 會根據主題來產生靜態檔案。
- package.json
Hexo 所需的套件資料
- _config.yml
設定專案的大部分配置，可以參考 Hexo 官網上的文件說明


## 常用指令

```bash
hexo new [layout] <文章標題>
hexo new post "我的第一篇文章 By Hexo"

// local server on http://localhost:4000/
hexo server
```


### 搭配github page

```bash
npm install hexo-deployer-git --save  //安裝 git 部署套件
```

複製 github Repository 的連結

_config.yml 設定爲以下調整，官網參考

```bash
# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: git
  repo: https://github.com/Kevinwuu/Kevinwuu.github.io.git # git@github.com:<github_username>/<github_username>.github.io.git
  branch: gh-pages
  message: 'deploy site'
```

執行以下指令將 Hexo 產生的網站內容上傳到 Github

```bash
hexo clean && hexo deploy
```

## 自訂 Domain 網域

## Refference

[[教學] 使用 GitHub Pages + Hexo 來架設個人部落格 | 瑪利歐的部落格 (ed521.github.io)](https://ed521.github.io/2019/07/hexo-install/)

[https://chanchandev.com/note/Hexo/hexo-introduction/2335841689/#Hexo-設定](https://chanchandev.com/note/Hexo/hexo-introduction/2335841689/#Hexo-%E8%A8%AD%E5%AE%9A)