---
title: mapbox hover顯示popup問題
date: 2022-06-05 17:18:14
categories: 前端
tags: mapbox
urlname: mapbox hover顯示popup問題
---

![Mapbox GL](mapboxgl.png)

## 原因

通常 mapbox 相關範例都是 click 某個點來顯示 popup，不過實際上也很常會需要在 hover 時顯示，同時 popup 上可能會有一些資訊可以點選

但是如果你設定 mousein 開啟,mouseleave 關閉 popup，那麼在你移動到 popup 前就會因為離開 popup 而觸發關閉

<!--more-->

## 解法

原先以為只是因為cluster本身跟popup中間有空隙導致觸發mouseout才發生
但其實這個問題有兩個原因造成

- 離開 popup
- 離開 map

mouseleave 不像原本所想的，是離開 layer 才觸發
而是離開特定 layer 或離開 map 都會觸發
由於 mapbox 的 popup 不像其他元件會畫在 canvas 中，而是畫在 map 外所以當滑鼠移動到popup上時也會判斷為離開 map。
看了看一些網路的文章後，有很多遇到跟我一樣問題的人，但都沒有看到有用的解法，所以最後決定自己實作

```javascript
const onMapLoad = () => {
if (!mapRef.current) return;
 const map = mapRef.current;
 /**
  * Add custom mouse event for cluster and popup
  * to avoid popup close when mouse moved on popup.
  */
 let isOnCluster = false;
 map.on("mousemove", (e) => {
   const features = map.queryRenderedFeatures(e.point, {
     layers: ["cluster-layer", "point-status-layer"],
   });

   if (isOnCluster) {
     // mouseleave cluster or point
     if (!features.length) {
       isOnCluster = false;
       map.getCanvas().style.cursor = "";
       setPopupInfo(null);
     }
   } else if (features.length) {
     // mouseenter cluster or point
     isOnCluster = true;
   }
 });
};
```

---

## Refference

一樣問題描述的文章
[Popup can stay when mouse goes to popup area from hovered point](https://github.com/mapbox/mapbox-gl-js/issues/11491)

[Mapbox add popup on hover (layer), close on mouseleave, but keep open on popup hover](https://stackoverflow.com/questions/69866651/mapbox-add-popup-on-hover-layer-close-on-mouseleave-but-keep-open-on-popup-h)

<https://www.notion.so/kevinwuuisme/Mapbox-GL-11edb60b7b054b4b85d278e44fb5ec0c#ee46847751d744b3b89894ed73f0d83f>
