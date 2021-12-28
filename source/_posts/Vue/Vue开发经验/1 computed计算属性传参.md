---
title: 1 computed计算属性传参
categories:
  - Vue
  - Vue开发经验
---

compute 计算属性使用的时候是不能传递参数的，但是我们使用闭包的特性可以完成参数传递

定义:闭包让你可以在一个内层函数中访问到其外层函数的作用域

让我们来看一个实例:
我们需要传递一个字符串到 shortName(name:string)这个函数中去，使用 shortName 函数只截取 name 的前 3 位，并补充...三个点作为省略

```html
<h1>{{ShortName("MikeEdu")}}</h1>
```

```javascript
const app = Vue.createApp({
	data() {
		return {
			name: "Mikeedu",
		}
	},
	computed: {
		ShortName() {
			return function (name) {
				return name.slice(0, 3) + ".".repeat(3)
			}
		},
	},
})
const vm = app.mount("#app")
```

运行结果:Mik....
