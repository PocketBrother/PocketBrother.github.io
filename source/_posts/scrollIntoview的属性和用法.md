---
title: scrollIntoView方法的使用
date: 2021-08-17 13:11:07
tags:
---

element.scrollIntoView()方法用于将调用他的元素滚动到浏览器窗口的可见区域,根据其他元素的布局,元素可能无法完全滚动到顶部或者底部,并且只作用在元素位于可滚动容器的内部.
## 示例:
```js
let element= document.getElementById('container');
//不传参
element.scrollIntoView();
//布尔
element.scrollIntoView(false);//可选值[true,false]
//[true]元素的顶部将对齐到可滚动祖先的可见区域的顶部。对应于scrollIntoViewOptions: {block: "start", inline: "nearest"}.
//[false]元素的底部将与可滚动祖先的可见区域的底部对齐。对应于scrollIntoViewOptions: {block: "end", inline: "nearest"}。
let options = {
    behavior:'auto',//定义过渡动画可选值[auto,smooth,instant]
    block:'center',//
    inline:'nearest'
    }
// 对象传参
element.scrollIntoView(options)
```
