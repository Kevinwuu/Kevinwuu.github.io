---
title: "[Hexo架站懶人包] - 加入utterances留言板功能"
date: 2022-06-12 21:52:43
categories: 前端
tags: hexo
---

![image2](image2.png)

基本設定非常快速，因此不多贅述操作流程，單純描述遇到的一些問題以及參考文章

常見的三個留言板第三方套件

- Disqus
- Gitalk
- utterances

選擇思路可以參考以下連接
[Hexo 新增 utterances 留言板與方案選擇思路](https://blog.kyomind.tw/hexo-blog-reply/)

<!--more-->

在`安裝與設定流程`的部分作者也提到了三篇參考文章，看完一二篇後，個人覺得第一篇就滿直接好懂了
其實主要流程也是照著[utteranc](https://utteranc.es/)網站上一步一步設定，最後再把script貼到指定的地方而已~

但如果只看教學文章而不是官網的話可能會漏掉幾個基本的注意事項導致設定失敗，看完前兩篇感覺都有漏掉一些東西所以這邊再稍微補充

- repo必須是public
- 確保[utterances app](https://github.com/apps/utterances)已經被安裝在你的repo下 (只需要開放權限給你需要用的repo就好)

在官網的最後一步中
要把產生的script檔，放在hexo主題下對應的swig檔
結果我看了一下我的theme資料夾後...
什麼都沒有啊xDDD

![image1.png](image1.png)

印象中之前似乎也遇到類似問題，不確定是因為hexo新版的檔案結構不同還是因為目前使用的主題問題
ps:之後確認完會再來修改本文

but最後還是順利找到地方設定了，原來各留言板功能也一併被整合在主題設定的config中
在我目前主題的config下 `_config.next`
只要填上repo的部分`owner/repo` 和你想要的設定就行了，預設的comment裡也很貼心地告訴你可以用的option有哪些
(option的內容可以參考[utteranc](https://utteranc.es/)官網說明)

```yml
# Utterances
# For more information: https://utteranc.es
utterances:
  enable: true
  repo: Kevinwuu/Kevinwuu.github.io
  # Available values: pathname | url | title | og:title
  issue_term: pathname
  # Available values: github-light | github-dark | preferred-color-scheme | github-dark-orange | icy-dark | dark-blue | photon-dark | boxy-light
  theme: github-light
```

### 讓分類與標籤頁沒有留言區

留言區開關早已納入了 Hexo 內建的語法設定
請在頁面所屬的 Markdown 檔案中，加入下列comments: false標籤，以分類頁為例：

```markdown
title: categories
layout: categories
comments: false
---
