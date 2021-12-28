---
title: 5 数组对象props的易错点
categories:
  - Vue
  - Vue3.0组件化开发
---

数组和对象都隶属于引用类型，当我们使用 props 设置 default 默认属性的时候，应该使用工厂函数进行返回

由于对象和数组是引用类型，如果直接返回对象和数组，如果有多个子组件实例，都同时拥有同样的地址，改动一个实例会造成其他实例的数据均被修改

让我们来看一个例子
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Dec-18-2021-15-15-01.gif)
从左到右以此顺序是 obj,arr,arr1 [引用对象，引用数组，使用工厂函数返回的数组]，我们可以发现引用对象和引用数组修改一个实例其他组的数据全部修改，所以对于引用类型和数组，我们需要使用工厂函数来进行返回

> 由于在子组件中直接修改 props 是无效的，所以我们使用 data 作为响应式数据的传递
> ![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/3cDUZs.png)
> 其中的 obj,arr,arr1 分别代表了 3 种例子

- obj:引用对象
- arr:引用数组
- arr1: 使用工厂函数返回的数组

```html
<div @click="change">{{content}}-{{content1}}-{{content2}}</div>
<span @click="change1">{{name}}</span>
```

```javascript
const app = Vue.createApp({
	data() {
		return {}
	},
	template: "<hd></hd> <hd></hd><hd></hd> <hd></hd>",
})
app.component("hd", {
	data() {
		return {
			content: this.obj,
			content1: this.arr,
			content2: this.arr1,
		}
	},
	props: {
		obj: {
			type: Object,
			default: { name: "Mikeedu", age: 18 },
		},
		arr: {
			type: Array,
			default: [5, 2, 6, 3, 1],
		},
		arr1: {
			type: Array,
			default: function () {
				return [5, 2, 7, 3, 8]
			},
		},
		name: {
			default: "mike",
		},
	},
	methods: {
		change() {
			this.content.name = "Olivia"
			this.content1.push(5)
			this.content2.push(6)
		},
	},

	template:
		"<div @click='change'>{{content}}-{{content1}}-{{content2}}</div> <span @click='change1'>{{name}}</span>",
})
const vm = app.mount("#app")
```
