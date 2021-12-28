---
title: 9 mustache中也可以使用表达式
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

mustache 中可以使用表达式

```
javascript data(){ return{ lesson:{ status:true } } }
```

```html
<div>{{ lesson.status ? "取消" : "删除" }}</div>
```
