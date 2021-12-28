---
title: 3 computed计算属性
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

关于 computed 计算属性，我们主要和 methods 进行比较学习

- computed 是属性访问，而 methods 是函数调用
  具体体现在 computed 以属性形式使用，而 methods 使用()方法的形式来进行调用

```javascript
methods:{
    m1(){
        return this.message
    }
},
computed:{
    c1(){
        return this.message
    }
}
```

```html
<!--方法使用()进行调用-->
<h1>{{m1()}}</h1>
<!--computed计算属性以属性的形式调用-->
<h1>{{c1}}</h1>
```

- computed 带有缓存功能，而 methods 不具有
  简而言之,computed 只有在依赖于 data 中的数据的时候，才会进行重新求值

这里我们使用一个最经典的例子，由于该用例并未依赖 data 中的数据，所以不会更新

```javascript
computed:{
    test(){
        return new Date().getTime()
    }
}
```

<hr/>
为了加深印象，我们在这里做一个例子，这个例子描述了在改变非对应的data时候,methods会更新非响应式数据，而computed会因为该数据非响应而不会进行更新

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Dec-14-2021-01-13-11.gif)

```html
<div id="app">
	<div class="button" @click="change()">CHANGEDATA</div>
	<div class="res">
		<div>计算属性:{{c1}}</div>
		<div>方法:{{m1()}}</div>
	</div>
	<div class="show">{{content}}</div>
</div>
```

```javascript
const app = Vue.createApp({
	data() {
		return {
			content: 1,
		}
	},
	methods: {
		change() {
			this.content += 1
		},
		m1() {
			return new Date().getTime()
		},
	},
	computed: {
		c1() {
			return new Date().getTime()
		},
	},
})
const vm = app.mount("#app")
```

```css
* {
	background-color: #2c3e50;
}
#app {
	display: flex;
	justify-content: center;
	align-items: center;
	height: 100vh;
	flex-direction: column;
	user-select: none;
}
.button {
	color: white;
	width: 400px;
	height: 80px;
	font-size: 50px;
	border: solid 1px #ddd;
	display: flex;
	justify-content: center;
	align-items: center;
}
#app > div {
	width: 400px;
	height: 80px;
	color: white;
	border: solid 1px #ddd;
	display: flex;
	align-content: space-around;
}
.res > div {
	width: 200px;
	border: solid 1px #ddd;
}
.show {
	display: flex;
	justify-content: center;
	align-items: center;
	font-size: 30px;
}
```
