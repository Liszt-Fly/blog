---
title: 8 非props属性传递技巧
categories:
  - Vue
  - Vue3.0组件化开发
---

所有非 props 属性都会存储在`$attrs`中

传递情况分为三种:

- 子组件的根标签有且仅有一个，所有的$attrs 附加在该根标签上

* 子组件的根标签有多个，$attrs 不会附加在任意一个根标签上，需要手动指定
* 子组件的标签有且仅有一个，但是在 JS 中设定了`inheritAttrs: false`,所做情况如 2，仍然需要手动进行指定

* 情况 1
  ![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/rsoBWo.png)

```javascript
const app = Vue.createApp({
	template: `<xj class="hd"></xj>`,
})
app.component("xj", {
	template: `<div>123</div>`,
})
const vm = app.mount("#app")
```

- 情况 2
  这种情况本身无唯一根元素是无法自动指定的，此时使用$attrs 手动指定
  ![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/6u6N5S.png)

```javascript
const app = Vue.createApp({
	template: `<xj class="hd"></xj>`,
})
app.component("xj", {
	template: `<div >123</div><div :class='$attrs.class'>456</div>`,
})
const vm = app.mount("#app")
```

- 情况 3
  启用该属性之后和情况 2 相同

```javascript
inheritAttrs: false
```

$attrs 的传递技巧: 如果使用`v-bind:'$attrs'`表示的是父层级的所有 attrs 属性均传递，如果使用`$attrs.class`表示的仅仅压入 class 属性

<hr/>
attrs 能传递所有非 props 属性，事件当然也可以传递

由于$attrs 传递到的是 123div，所以在点击 123 的 div 时候 alert，点击 456 的时候无响应

```javascript
const app = Vue.createApp({
	template: `<xj class="hd" @click='alert'></xj>`,
	methods: {
		alert() {
			alert(5)
		},
	},
})
app.component("xj", {
	template: `<div v-bind="$attrs">123</div><div :class='$attrs.class'>456</div>`,
})
const vm = app.mount("#app")
```
