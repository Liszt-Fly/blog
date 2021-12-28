---
title: 2 vue指令
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

vue 中为了方便提供了许多常用指令，这里介绍一部分

## v-text

<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-text</span>指令和`{{}}`的作用是相同的，将 data 中的数据渲染出来

```javascript
data(){
    return {
        name:"Mike"
    }
}
```

二者效果是一致的

```html
<div v-text="name"></div>
<div>{{name}}</div>
```

## v-html

<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-html</span>和 <span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-text</span>的效果是类似的，但是 v-text 并不能渲染 html 语法的内容
举个例子

```html
//content1 <font color="red">Hello</font>
```

针对该文本内容<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-html</span>可以渲染出红色的文本 Hello，而<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-text</span>命令渲染出的仅仅是该 html 文本内容

## 响应式特性

Vue 中的 data 都具有相应性，修改 data 的数据，template 模版中的内容都会即时响应修改

```javascript
setTimeout(() => {
	vm.$data.name = "向军大叔"
}, 3000)
```

```html
<div v-text="name"></div>
```

经过三秒，模版中的 name 自动更换成向军大叔

## v-show & v-if

<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-show</span>和<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>v-if</span>的作用都是根据布尔值来控制元素是否显示，true=>显示,false=>隐藏

```html
//隐藏元素
<div v-show="false">HELLO</div>
```

## v-once

v-once 的意义是仅渲染一次,上面说明了 vue 中的 data 是响应性的，如果我们在 data()中修改了数据内容，模版内容会相应修改，我们可以再看响应性中例子，将 div 添加 v-once 指令

```javascript
setTimeout(() => {
	vm.$data.name = "向军大叔"
}, 3000)
```

```html
<div v-text="name" v-once></div>
```

## v-bind

v-bind 指令用于动态绑定属性，<span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>动态属性要使用[变量名]</span>,对于 <span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>动态事件要使用[变量名]</span>

这里使用两个例子，一个 class 动态类型绑定，一个按键动态类型绑定

### class 动态类型绑定

实现点击文字变色的效果，核心原理是点击文字，动态绑定的 class 会发生改变，不同的 class 对应不同颜色的文字
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Dec-12-2021-17-55-34.gif)

style 样式文件

```css
* {
	background-color: #34495e;
}
#app {
	display: flex;
	height: 100vh;
	justify-content: center;
	align-items: center;
}
h1 {
	font-size: 80px;
	user-select: none;
}
.v-1 {
	color: #2ecc71;
}
.v-2 {
	color: #f1c40f;
}
.v-3 {
	color: #8e44ad;
}
.v-4 {
	color: #ecf0f1;
}
```

html

```html
<body>
	<div id="app"><h1 :class="[style]" @click="addNumber">{{title}}</h1></div>
</body>
```

js

```javascript
const app = Vue.createApp({
	data: function () {
		console.log(this)
		return {
			title: "MIKEEDU",
			number: 1,
			prefix: "v-",
		}
	},
	computed: {
		style() {
			return this.prefix.concat(this.number)
		},
	},
	methods: {
		addNumber() {
			this.number < 4 ? (this.number += 1) : (this.number = 1)
		},
	},
})

const vm = app.mount("#app")
```

### 动态事件绑定

该例子我们需要做到，将一个本身使用 click 触发的事件转变成 mouseover 触发事件

```html
<div id="app">
	<div class="button" @[test]="change">{{content}}</div>
</div>
```

```javascript
const app = Vue.createApp({
	data() {
		return {
			test: "click",
			content: "Dynamic Event",
		}
	},
	methods: {
		change: function () {
			alert("触发事件")
			setTimeout(() => {
				this.test = "mouseover"
				this.content = "mouseover"
			}, 1000)
		},
	},
})
const vm = app.mount("#app")
```
