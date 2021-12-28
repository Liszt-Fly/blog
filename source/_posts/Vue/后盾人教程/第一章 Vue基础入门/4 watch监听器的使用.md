---
title: 4 watch监听器的使用
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

监听器的意义是在所监听的目标属性发生改变时，触发监听器函数，执行对应操作

```html
<div id="app">
	<button @click="add">增加</button>
	<h1>{{num}}</h1>
</div>
```

```javascript
const app = Vue.createApp({
	data() {
		return {
			num: 0,
		}
	},
	watch: {
		num(newValue, oldValue) {
			console.log(`新值是${newValue},旧值是${oldValue}`)
		},
	},
	methods: {
		add() {
			this.num++
		},
	},
})
const vm = app.mount("#app")
```

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Qh5xIY.png)
每当监听的 value 值改变，都会触发监听器进行打印消息
