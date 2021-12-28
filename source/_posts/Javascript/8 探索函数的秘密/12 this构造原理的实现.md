---
title: 12 this构造原理的实现
categories:
  - Javascript
  - 8 探索函数的秘密
---

this 的指向是可以被改变的，本节我们使用`call`函数来改变 this 的指向

首先给出一个构造函数,然后使用构造函数 new 一个实例，此时 this 指向新的实例对象 lisi

```javascript
function User(name) {
	this.name = name
}
let lisi = new User("李四")
```

我们调用 call 函数将 this 指向新的对象

```javascript
let hdcms = { url: "hdcms.com" }
User.call(hdcms, "开源系统")
console.log(hdcms){url:"hdcms.com",name:"开源系统"}
```
