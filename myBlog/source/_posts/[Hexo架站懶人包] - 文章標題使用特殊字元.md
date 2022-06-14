---
title: "[Hexo架站懶人包] - 文章標題使用特殊字元"
date: 2022-06-13 00:05:44
categories: 前端
tags: hexo
urlname: hexo-special-symbol-in-title
---

![hexo_github](../images/hexo_github.png)

## Root cause

若在文章標題中使用特殊符號時 (例如：[] 中括號)，會出現錯誤訊息
主要是跟yml的格式有關，因此修改檔案或資料夾名稱不會有問題
但在`hexo new post`或是修改舊文章標題後`hexo s`都會跳錯
`err: YAMLException: bad indentation of a mapping entry`

<!--more-->

```text
FATAL {
  err: YAMLException: bad indentation of a mapping entry (1:20)

   1 | title: [Hexo架站懶人包] - 文章標題使用特殊字元
  ------------------------^
   2 | date: 2022-06-12 16:03:00
   3 | categories:
 ...
 ...
 ...
 ...
     
    reason: 'bad indentation of a mapping entry',
    mark: {
      name: null,
      buffer: 'title: [Hexo架站懶人包] - 文章標題使用特殊字元\n' +
        'date: 2022-06-12 16:03:00\n' +
        'categories: \n' +
        'tags: \n',
      position: 19,
      line: 0,
      column: 19,
      snippet: ' 1 | title: [Hexo架站懶人包] - 文章標題使用特殊字元\n' +
        '------------------------^\n' +
        ' 2 | date: 2022-06-12 16:03:00\n' +
        ' 3 | categories: '
    }
  }
} Something's wrong. Maybe you can find the solution here: %s https://hexo.io/docs/troubleshooting.html

```

## 解法

在建立文章後再去修改文章標題
將標題以單引號 `''` 或雙引號 `""` 包裹起來

```md
title: "[Hexo架站懶人包] - 文章標題使用特殊字元"
```

## 備註

此解法只能先用一般字元建立文章後再去修改，對於new post指令無效

自己曾試過將指令中的雙引號改為單引號看看

```bash
hexo new post '[Hexo架站懶人包] - 文章標題使用特殊字元'
```

雖然可以順利建立，但由於parsing問題標題會被截斷
只剩下

```text
文章標題使用特殊字元'
```
而且也沒創建對應的assest資料夾

ps: 每次都需要重新命名畢竟還是有點麻煩，還在尋找其他方法中

## 參考

[在 Hexo 文章標題使用特殊字元的技巧](https://carolchyang.github.io/2021/04/10/hexo-title-error/)
