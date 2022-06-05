---
title: Hexo架站 - RSS
date: 2022-06-05 00:35:36
categories:
tags:
---

![](rss.png)

## What's RSS

RSS的英文全稱是Really Simple Syndication
簡單來說，就是可以將網頁內容抽取出來變成一份xml檔，讓使用者透過RSS Feed的功能並配合RSS閱讀器，就可以直接在同一個地方，訂閱和閱讀自己有興趣的所有消息來源。

<!--more-->

## Why RSS

RSS是每個傳統部落格必備的功能，以前時常可以在網站上看到一個很像wifi的圖示出現在某個角落
透過這個功能，大家可以像現實中收報紙一般，不用特地打開網站也能知道你所喜愛的作者有發布新的內容

以往我們獲取知識和消息常常常常需要在不同平台切換
像是Medium、網頁or部落格、電視新聞、FB粉專、Twitter...等

在以前網路剛開始時可能覺得還好，可是當資訊大爆炸的時代開始，RSS又開始流行了起來
這次大家不只是把它拿來當作單純的訂閱工具，同時也是從被動閱讀轉換為主動閱讀的必備良藥

### 被動閱讀

在現今科技蓬勃發展下，AI和演算法操控著我們絕大部分網路世界的內容來源
因此我們只會不斷看到以下幾種內容

- 聳動、血腥、八卦的
- 演算法根據以往內容判斷我們應該會喜歡的
- 廣告公司希望我們看到的

### 主動閱讀

主動閱讀意味者我們必須挺身對抗這一切，重新找回自主權
以往我們想獲取知識時可能會選擇自己挑選對應的書籍
但在現今，我們可能需要去挑選的是 
=> 合適的媒體來源

不管是Youtuber、新聞頻道、個人部落格、內容發布平台都好

主動去建立自己的媒體來源吧

## RSS reader

平時最常拿來閱讀的裝置大概就是手機或Ipad了
目前看到有名的有Feedly和Inoreader，版面和操作上個人比較喜歡用Inoreader。

## Installation 

安裝[hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)

```
npm install hexo-generator-feed --save
```

## Configuration

在 Hexo 目錄下的 _config.yml 文件中加入以下代碼

```
# RSS
# https://github.com/hexojs/hexo-generator-feed
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
  icon: icon.png
  autodiscovery:true
  template:
```

<!--more-->