---
title: 10 event事件
categories:
  - Vue
  - Vue3.0组件化开发
---

在 Vue 中通过 props 来父组件向子组件传值，那么子组件通知父组件，可以使用 event 事件来实现

子组件中使用`$emit`，父组件中使用`@事件名`进行接收

```javascript
const app = Vue.createApp({
	template: "<xj @output='out'></xj>",
	methods: {
		out(v) {
			alert(v)
		},
	},
})
app.component("xj", {
	template: "<div @click='transport'>THIS IS A BUTTON</div>",
	emits: ["output"],
	methods: {
		transport() {
			this.$emit("output", 5)
		},
	},
})
app.mount("#app")
```

<font color='#ea8685'>重点:事件一定要在 emits 选项中注册</font>
原因：对于子组件中未被定义为组件触发的所有事件监听器，Vue 现在将把它们作为原生事件监听器添加到子组件的根元素中

我们来对比一下是否在 emits 中注册的区别:

- 在 emits 中注册
  ![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/3CBBKR.png)

* 不在 emits 中注册
  可以发现如果不在 emits 中进行注册，事件会被压入子组件的`$attrs`
  ![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/ckMdRe.png)
