---
title: "[Hexo架站懶人包] - Sitemap設定"
date: 2021-07-20 22:55:46
categories: 前端
tags: hexo
# urlname: hexo-sitemap
urlname: "2021/07/20/hexo-sitemap"
---

![sitemap](sitemap.png)

## 步驟

1. 安裝自動產生sitemap的套件[hexo-generator-sitemap](https://github.com/hexojs/hexo-generator-sitemap)

```bash
npm install hexo-generator-sitemap --save
```

2. 設定根目錄下的_config.yml，自己是習慣把新的設定加在設定檔最後面(注意縮排!)

<!--more-->

```yaml
# Sitemap
# https://github.com/hexojs/hexo-generator-sitemap
sitemap:
    path: sitemap.xml
    template: ./sitemap_template.xml # 這行非必填，除非你想設定自訂的樣板
```

3. 重新發布，產生新內容，
檢查/public下有沒有正確產生sitemap.xml。

## Google Search Console設定

在一開始進入 Google Search Console 之前必須先設定驗證自己的網站

![sitemap-1](sitemap-1.png)

### 驗證

根據ithome的[文章](https://ithelp.ithome.com.tw/articles/10249885)範例是建議使用網址前置字元做驗證。
不過在查教學文章前我就先使用網域的驗證方式成功了! :good
個人是覺得比教學簡單很多，只要輸入完網域後就會自動驗證成功。
特別標註為新功能，可能就是代表會比舊方法好用吧?

![sitemap-2](sitemap-2.png)

### 填寫sitemap位置

首先先點選側邊欄中的Sitemap
![](sitemap-3.png)


![](sitemap-4.png)

如果成功提交後就會將結果顯示在已提交的Sitemap中

## Trouble Shooting

- 如果填寫sitemap位置失敗，記得檢查是否有填入完整網址(像是我一開始就是忘了填`https://)
	```
	https://<yoursite_domain>/sitemap.xml
	```



- 提交成功，但是顯示狀態錯誤

![sitemap-err](sitemap-err.png)

![sitemap-err-1](sitemap-err-1.png)

在提交後有，若出現這個錯誤：「可讀取 Sitemap，但其中含有錯誤」，表示 sitemap 裡面的網址跟當初在 Google Search Console 註冊的網址有所差異。

自己目前為止遇到過兩次:

1. 從github page網址改為自訂網域
2. 更換自訂網域

當網域名稱一更換，當初sitemap中舊文章網址連結就會找不到對應內容，必須回到_config.yml 更新 URL，才能跟sitemap填寫的網址匹配
記得重新deploy後要回來Google domain重新提交
本來deploy後是想說慢慢等他錯誤應該就會消失，但後來想說重新提交看看好了，結果馬上狀態就成功了

- deploy完，sitemap.xml 找不到頁面
這篇文章有非常完整的解決方案，我自己是沒有遇到
如果有遇到的朋友可以參考看看
[解決 Hexo + Github Pages 新增 sitemap.xml 找不到頁面](https://blog.kyomind.tw/adding-sitemap-issue/)

----
Refference

[輕鬆地提交 Hexo 部落格的 Sitemap.xml 到 Google Search Console](https://askie.today/upload-sitemap-google-search-console-seo-hexo-blog/)
[(24) 試著學 Hexo - SEO 篇 - Google Search Console](https://ithelp.ithome.com.tw/articles/10249885)
[SEO 優化 (一)：為什麼搜尋 (Google) 不到我的 Hexo 部落格？](https://jenifers001d.github.io/2019/12/09/SEO/SEO1-Website-is-Not-Showing-in-Google-Search/)
[參考連結](https://ycjhuo.gitlab.io/blogs/The-first-step-of-SEO-how-to-tell-Google-the-way-to-find-your-website.html#%E6%8F%90%E4%BA%A4-sitemap-%E5%BE%8C-%E5%8F%AF%E8%83%BD%E7%94%A2%E7%94%9F%E7%9A%84%E9%8C%AF%E8%AA%A4%E8%A8%8A%E6%81%AF)
