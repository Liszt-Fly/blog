---
title: 1 初识vue
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

首先需要使用<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>CDN</span>引入 Vue

```html
<script src="https://unpkg.com/vue@next"></script>
```

Vue 的 js 引入需要两个步骤:

1. 创建 App 并在 App 内容中进行配置(template,style....)
2. 将 app 挂载到 DOM 元素上

```js
Vue.createApp({
	data() {
		return {
			title: "后盾人",
		}
	},
	// template: `<div>houdunren.com-{{title}}</div>`
}).mount("#app")
```

这样创建的是 Vue 的根元素，然后进行挂载

可以更详细的进行创建，并且创建父组件和子组件

创建父组件

```js
//根组件
const app = Vue.createApp({
	data() {
		return {
			name: "根组件-父亲",
		}
	},
	template: `<div>{{name}}- <xj/></div>`,
})
```

创建子组件

```javascript
//子组件
app.component("xj", {
	data() {
		return {
			name: "向军大叔",
		}
	},
	template: `<div style="background-color:red;color:white">{{name}}</div>`,
})
```

进行挂载

```javascript
const vm = app.mount("#app")
```
