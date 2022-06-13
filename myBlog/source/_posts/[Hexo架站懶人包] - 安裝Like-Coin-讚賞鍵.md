---
title: "[Hexo架站懶人包] - 安裝Like Coin 讚賞鍵"
date: 2022-06-13 22:43:00
categories: 前端
tags: hexo
urlname: hexo-integrate-like-coin
---

![hexo_github](hexo_github.png)

[Like Coin官網教學](<https://docs.like.co/v/zh/user-guide/creator/self-host/hexo-next>)的內容引用自[只是個打字的](https://blog.typeart.cc/) 的教學文章，講解的已經滿清楚

But!
之前在許多文章都提過，HEXO NEXT 版本6 → 8之後就有了滿大的改動，許多常用的套件設定都已經整合進config中
因此很多網路上看到的教學文章採用的設定方法已經不太適用
<!--more-->

[安裝教學(old)](https://blog.typeart.cc/%E5%9C%A8Hexo%20NexT%E5%A2%9E%E5%8A%A0like%20Button/)

[安裝教學(new)](https://blog.typeart.cc/upgrade-nexo-next-6-to-8-and-integrate-adsense-like-button/)

But!
新版教學文章雖然標題有寫到Like Coin如何引入，但內文可以說幾乎一行都沒提到XD
但他有提到了一個新的重點就是，新版NEXT主題提供了[custom files](<https://theme-next.js.org/docs/advanced-settings/custom-files.html>)的寫法，讓你可以把以前很多侵入式的script寫法拉出來管理

詳細設定可以在`_config.next.yml`中找到，照著comment新增對應的資料夾和檔案即可
一般看到的Like Coin大多都放在文章結尾的下方，因此footer或postBodyEnd都可以使用看看

```yml
# Define custom file paths.
# Create your custom files in site directory `source/_data` and uncomment needed files below.
custom_file_path:
  #head: source/_data/head.njk
  #header: source/_data/header.njk
  #sidebar: source/_data/sidebar.njk
  #postMeta: source/_data/post-meta.njk
  # postBodyEnd: source/_data/post-body-end.njk
  footer: source/_data/footer.njk
  #bodyEnd: source/_data/body-end.njk
  #variable: source/_data/variables.styl
  #mixin: source/_data/mixins.styl
  #style: source/_data/styles.styl
```

footer : 會放在外面
![image_footer](image_footer.png)

postBodyEnd : 跟文章的背景一樣是灰色的
![image_post](image_post.png)


