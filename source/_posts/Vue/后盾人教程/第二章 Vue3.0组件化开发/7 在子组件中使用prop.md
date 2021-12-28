---
title: 7 在子组件中使用prop
categories:
  - Vue
  - Vue3.0组件化开发
---

在上一节中学习了，子组件中的 props 是 readonly 的，但是如果我们想在子组件中修改 props，并且让它具有响应式的特性，就需要使用其他的方法来达到目的了

⭐ 解决策略:在子组件中 data 定义一个数据，这个数据初始值定义为 props,这样就可以使用了

思路是通过了对子组件的 props 包裹成为了响应数据 data，从而在子组件中可以使用响应式 props 的数据

```javascript
const app = Vue.createApp({
	data() {
		return {}
	},

	template: "<as name='mike' ></as>",
})
app.component("as", {
	data() {
		return {
			mName: this.name,
		}
	},
	methods: {
		change() {
			this.mName = "JAVA"
			console.log("ok")
		},
	},

	props: {
		name: String,
	},
	template: `<div @click='change'>{{mName}}</div>`,
})
let vm = app.mount("#app")
```

当这个问题解决了之后，又出现了新的问题，如果我们希望在父组件中修改 props 通知子组件修改怎么办？

这个时候的子组件是不会响应的，因为 props 修改而不是 data 中的 mName 发生了修改

🌟 解决方案:使用 watch 对 props 进行监听，如果修改，就对 data 进行修改，将 data 更新为新的 props

```javascript
const app = Vue.createApp({
	data() {
		return {
			name: "MIKE",
		}
	},
	methods: {
		change() {
			this.name = "JAVAEDU"
		},
	},
	template: "<as :name='name' @click='change' ></as>",
})
app.component("as", {
	watch: {
		name() {
			//props进行修改之后

			this.mName = this.name
		},
	},
	data() {
		return {
			mName: this.name,
		}
	},
	methods: {
		change() {
			this.mName = "JAVA"
			console.log("ok")
		},
	},

	props: {
		name: String,
	},
	template: `<div @click='change'>{{mName}}</div>`,
})
let vm = app.mount("#app")
```
