---
title: "mapbox-gl hover顯示popup"
date: 2021-07-20 22:55:46
categories: 前端
tags: mapbox
---

## 原因

通常 mapbox 相關範例都是 click 某個點來顯示 popup，不過實際上也很常會需要在 hover 時顯示，而且 popup 上可能會有一些資訊可以點選

但是如果你設定 mousein 開啟,mouseleave 關閉 popup，那麼在你移動到 popup 前就會因為離開 popup 而觸發關閉

## 解法

其實這個問題有兩個原因造成

- 離開 popup
- 離開 map

mouseleave 其實不像原本所想的，是離開 layer 才觸發
而是離開特定 layer 或離開 map 都會觸發
由於 mapbox 的 popup 不像其他元件會畫在 canvas 中，而是畫在 map 外所以會判斷為離開 map。

看了看一些網路的文章後，有很多遇到跟我一樣問題的人但都沒有看到有用的解法，所以最後決定自己實作

---

## Refference

https://www.notion.so/kevinwuuisme/Mapbox-GL-11edb60b7b054b4b85d278e44fb5ec0c#ee46847751d744b3b89894ed73f0d83f
