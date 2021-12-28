---
title: 6 props数据流是单向的
categories:
  - Vue
  - Vue3.0组件化开发
---

props 数据流是单向的，可以在父组件中修改子组件的内容，是有相应特性的，而在子组件中 props 是不可修改的(readOnly)

在该例子中，网页显示内容为 mikebookpro，我们在父组件中修改内容，子组件和父组件内容都更新，但是在子组件中修改 props，报出 warning 不允许修改，所以数据流向是单向的

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Dec-18-2021-5-53-52.gif)

```javascript
const app = Vue.createApp({
	data() {
		return {
			name: "mikebookPro",
		}
	},
	template:
		"<xj :content='name'></xj><hr/>父组件中的值:{{name}}<button @click='name=`MAC`'>父组件修改值</button>",
})
app.component("xj", {
	props: {
		content: String,
	},
	template:
		"<div >{{content}}</div> <hr/>子组件中的值:{{content}} <button @click='content=`mac`'>子组件修改值</button>",
})
const vm = app.mount("#app")
```
