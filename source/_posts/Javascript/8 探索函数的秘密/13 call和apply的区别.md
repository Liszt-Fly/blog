---
title: 13 call和apply的区别
categories:
  - Javascript
  - 8 探索函数的秘密
---

apply 和 call 都会立刻执行，对于 call 方法来说，多个参数使用逗号隔开，而对于 apply 方法来说，多个参数使用数组存储

```javascript
let lisi = {
	name: "李四",
}
let wangwu = {
	name: "王五",
}
function User(web, url) {
	console.log(this.name + web + url)
}
User.call(lisi, "https://houdunren.com", "https://www.baidu.com") //改变this指向李四，并且立刻执行函数

User.apply(lisi, ["后盾人", "hdcms.com"]) //同样改变this，并且立刻执行
```

再来看一个 DOM 的例子

```html
<button>hdcms</button><button>houdunren</button>
```

```javascript
function show() {
	alert(this.innerHTML)
}
let buttons = document.querySelectorAll("button")
buttons.forEach((item) => {
	item.addEventListener("click", (event) => {
		show.call(event.target) //this->dom对象，输出button的innerHTML
	})
})
```

除此之外，由于 apply 可以接收数组参数的特性，可以起到点语法展开数组的作用,max 方法只适用于多个参数[非数组]，使用 apply 可以将数组转化为多参数形式，从而达到目的

```javascript
let arr = [1, 2, 3, 4, 15]
console.log(Math.max.apply(null, arr)) //apply将数组变成多个参数
```
