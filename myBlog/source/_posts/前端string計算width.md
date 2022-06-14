---
title: 前端string計算width
date: 2022-06-05 17:56:33
categories: 前端
tags: js
urlname: frontend-calculate-string-width
---

![debug](debug.png)

## Target

工作上遇過兩次不同的情況，一樣都是需要判斷字串是否overflow
但依據狀況的不同，適合使用的解法也會有所不同

<!--more-->

## Solution

網路上有提供了不只一種方法，根據不同情況

1. 判斷table中字串是否overflow，如有overflow hover時才要顯示tooltip，反之則不用
Only show ReactTooltip when text overflow

```javascript
const checkOverflow = (e) => {
	const isOverflow = false;
	isOverflow = e.offsetHeight < e.scrollHeight || e.offsetWidth < e.scrollWidth;
	// do something
}
```

2. 判斷table中tag欄位內容是否overflow，如果確認過長則在結尾多顯示一個 `...` tag，hover後顯示剩餘項目的tooltip

印象中網路上提供了不只一種方式，這次是使用convas

```javascript
const font = '13px Roboto';
const canvas = document.createElement('canvas');
const context = canvas.getContext('2d');
context.font = font;
const { width } = context.measureText(inputText);
```

---

## Refference

[How to detect overflow of React component without ReactDOM?](https://stackoverflow.com/questions/42012130/how-to-detect-overflow-of-react-component-without-reactdom)

平常使用的tooltip套件，看起來沒有提供相關的method
[react-tooltip](https://github.com/wwayne/react-tooltip)

[相關的truncate套件](https://www.npmtrends.com/react-ellipsis-text-vs-react-ellipsis-with-tooltip-vs-react-lines-ellipsis-vs-react-text-truncate-vs-react-truncate-vs-react-truncate-string)


最接近想要的效果，但要多包一層element可能會影響排版
[react-ellipsis-with-tooltip](https://github.com/amirfefer/react-ellipsis-with-tooltip)
