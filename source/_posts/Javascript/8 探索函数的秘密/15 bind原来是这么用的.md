---
title: 15 bind原来是这么用的
categories:
  - Javascript
  - 8 探索函数的秘密
---

bind 的效果类似于 call，但是它<u>并不是立即执行的</u>,所以 bind 特别适合非立即执行的场景使用

```javascript
function show() {
	console.log(this.name)
}
//bind不是立即执行的,除了这一点和call一致
show.bind({ name: "houdunren" })() //houdunren
```

```javascript
function hd(a, b) {
	return this.f + a + b
}
console.log(hd.bind({ f: 1 }, 1, 1)())
```

再看一个结合 DOM 使用的例子

```html
<body>
	<button>后盾人</button>
</body>
```

```javascript
document.querySelector("button").addEventListener(
	"click",
	function () {
		alert(this.url)
	}.bind({ url: "houdunren.com" })
)
```
