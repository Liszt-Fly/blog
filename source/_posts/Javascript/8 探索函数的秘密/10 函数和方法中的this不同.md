---
title: 10 函数和方法中的this不同
categories:
  - Javascript
  - 8 探索函数的秘密
---

this 的指向在普通函数和方法中时指向是不一样的

首先让我们看看全局中的 this
全局中的 this 指向 window

```javascript
console.log(this) //window
```

然后来看看普通函数中的 this
普通函数中的 this 仍然指向 window

```javascript
function show() {
	console.log(this)
}
```

接下来看看构造函数中的 this
构造函数中的 this 指向的是**实例**

```javascript
function User(name) {
	this.name = name
	this.show = function () {
		console.log(name)
	}
}
let lisi = new User("李四")
lisi.show()
```

对象和构造函数是类似的
对象中方法的 this 指向了对象 obj

```javascript
let obj = {
	name: "后盾人",
	show: function () {
		console.log(this) //this指向的是obj这个对象
	},
}
```

> ⚠️ 特别注意：是方法中的 this，方法中嵌套的函数就不是方法了，而是普通函数

让我们来看看这个例子
render 函数是方法下的普通函数，this 指向的仍是 window，而不是 obj 对象

```javascript
let obj = {
	name: "后盾人",
	show: function () {
		//this指向当前的对象
		that = this
		console.log(this)
		//this指向window
		function render() {
			console.log(this)
		}
		render() //window
		return this.name
	},
}
```

补救措施：如果我们想要保存指向 obj 的 this，我们可以在 this 指向 obj 的时候保存为 that,然后使用 that 来处理

```javascript
let obj = {
	name: "后盾人",
	show: function () {
		//this指向当前的对象
		that = this
		console.log(this)
		//this指向window
		function render() {
			console.log(this)
			console.log(that.name + "-render函数中调用")
		}
		render()
		return this.name
	},
}
```
