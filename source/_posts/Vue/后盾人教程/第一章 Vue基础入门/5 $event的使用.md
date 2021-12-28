---
title: 5 $event的使用
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

📎 定义:$event 指的是当前所触发的事件

```html
<div @click="change($event,"hello")></div>
```

在 js 中只需要随便使用一个形参接收对应的变量即可

```javascript
change(event, name){
  console.log(event,name);
}
```
