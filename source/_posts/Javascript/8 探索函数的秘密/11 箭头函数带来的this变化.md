---
title: 11 箭头函数带来的this变化
categories:
  - Javascript
  - 8 探索函数的秘密
---

先说结论：使用箭头函数，将会让函数的 this 来自于上下文，继承上文的 this 内容

```javascript
const test = () => {
	console.log(this)
}
test() //箭头函数继承上一级的this,test函数的上一级是window
```

```javascript
//在箭头函数中的this指向上下文中的this
let Lesson = {
	site: "后盾人",
	lists: ["js", "html", "css"],
	show: function () {
		//this继承上一级this所以指向obj
		return this.lists.map((title) => `${this.site}=${title}`)
	},
}
console.log(Lesson.show())
```

<hr/>
让我们看一个稍微复杂的例子，一个箭头函数和 DOM 例子的结合

由于使用箭头函数，我们的 this 指向上一级，肯定最终指向 obj 对象，可是我们要调用这个 button 本身怎么办？=>传递 event 参数，使用 event.target 即可获得 dom 元素 button

```html
<button>houdunren.com</button>
```

```javascript
let obj = {
	site: "后盾人",
	bind: function () {
		const button = document.querySelector("button")
		//button.addEventListener()相当于是button.onClick=>对象是button所以使用function()的时候指向的是按钮
		button.addEventListener("click", (event) => {
			console.log(event.target) //button
			event.target.innerHTML = this.site
			console.log(this) //父级作用域中的this 如果使用function()形式，this指向的是button
		})
	},
}
```

<hr/>
再来看一个例子，如果我们最终上下文的环境this指向的是dom元素本身，那么我们如何获取到obj对象呢？
可以使用self指针保存this，这个this指向的是obj对象即可
```html
	<div>this is houdunren</div>
		<div>this is mike</div>
```

```javascript
let dom = {
	site: "后盾人",
	mbind: function () {
		const self = this
		let divs = document.querySelectorAll("div")
		divs.forEach(function (el) {
			el.addEventListener("click", () => {
				console.log(self.site)
				console.log(this) //指向window 因为this使用上一级的this指向，上一级指向window
			})
		})
	},
}
```
