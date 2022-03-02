---
title: 原生JS取消默认事件和冒泡
date: 2021-08-05 23:22:06
tags:
---
# JS取消默认事件和冒泡

## 阻止冒泡:

w3c的方法是e.stopPropagation()，IE则是使用e.cancelBubble = true
stopPropagation也是事件对象(Event)的一个方法，作用是阻止目标元素的冒泡事件，但是会不阻止默认行为。什么是冒泡事件？如在一个按钮是绑定一个”click”事件，那么”click”事件会依次在它的父级元素中被触发 。
```js
window.event? window.event.cancelBubble = true : e.stopPropagation();
```
## 取消默认事件:

w3c的方法是e.preventDefault()，IE则是使用e.returnValue = false;
preventDefault它是事件对象(Event)的一个方法，作用是取消一个目标元素的默认行为。既然是说默认行为，当然是元素必须有默认行为才能被取消，如果元素本身就没有默认行为，调用当然就无效了。什么元素有默认行为呢？如链接<a>，提交按钮<input type=”submit”>等。当Event 对象的 cancelable为false时，表示没有默认行为，这时即使有默认行为，调用preventDefault也是不会起作用的。
```js
//假定有链接<a href="http://caibaojian.com/" id="testA" >caibaojian.com</a>
var a = document.getElementById("testA");
a.onclick =function(e){
    if(e.preventDefault){
        e.preventDefault();
    }else{
        window.event.returnValue == false;
    }
}
```

## return false的应用

javascript的return false只会阻止默认行为，而是用jQuery的话则既阻止默认行为又防止对象冒泡。

## 总结

```js
    //停止冒泡
    function stopBubble(e) { 
        //如果提供了事件对象，则这是一个非IE浏览器 
        if ( e && e.stopPropagation ){
            //因此它支持W3C的stopPropagation()方法 
            e.stopPropagation(); 
        } 
        else {
            //否则，我们需要使用IE的方式来取消事件冒泡 
            window.event.cancelBubble = true; 
        }
    }
    
    //阻止浏览器的默认行为 
    function stopDefault( e ) { 
    //阻止默认浏览器动作(W3C) 
        if ( e && e.preventDefault ) 
            e.preventDefault(); 
        //IE中阻止函数器默认动作的方式 
        else 
            window.event.returnValue = false; 
        return false; 
    }

```




