---
title: 10 classList样式
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

class 可以使用 v-bind 绑定 vue 中属性

表示如果 lesson.status 为 true，则启用 underline 的样式

```html
<div :class="{underline:lesson.status}"></div>
```

当然也可以启用多组样式

```html
<div :class="{underline:lesson.status,bigFont:lesson.bFont}"></div>
```

但是有些样式是基本样式，我们不需要根据 data 来进行控制

这种表示的是无论如何都启用 text-decoration 的样式，但是是否启用 underline 样式，要根据 lesson.status 来决定

```html
<div :class="['text-decoration',{underline:lesson.status}]"></div>
```

<hr/>
这里我们来看一个案例
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Dec-14-2021-13-24-51.gif)
我们希望根据课程的status来设置是否使用删除线

```css
* {
	background-color: #2c3e50;
	color: white;
	user-select: none;
}
.course {
	border: solid 3px #ddd;
	margin: 10px;

	position: relative;
	height: 40px;
	text-align: center;
}
.button {
	display: inline-block;
	position: absolute;
	right: 0;
	border: solid 1px #ddd;
	height: 100%;
	padding: 0 10px 0 10px;
	line-height: 40px;
}
.delete {
	text-decoration: line-through;
}
```

```html
<div id="app">
	<div :class="['course',{delete:!lesson.status}]" v-for="lesson in lessons">
		课程名:{{lesson.name}} 价格:{{lesson.price}}
		<div class="button" @click="lesson.status=!lesson.status">
			{{lesson.status?"删除":"添加"}}
		</div>
	</div>
</div>
```

```javascript
const app = Vue.createApp({
	data() {
		return {
			lessons: [
				{
					name: "如何学好C++",
					price: 100,
					status: true,
				},
				{
					name: "javascript精粹",
					price: 125,
					status: true,
				},
				{
					name: "mysql入门",
					price: 250,
					status: true,
				},
			],
		}
	},
})
const vm = app.mount("#app")
```

<hr/>
除此之外，我们还可以使用classList来管理样式

```html
<div :class="[classLists, 'text-decoration']">BACKGROUND</div>
```

这里的 classLists 是一个对象

```javascript
classLists: {
	current: true,
    border:true
}
```

分别对应 current,border 两种样式

```css
.current {
	background-color: black;
	color: white;
}
.border {
	border-radius: 5px;
	padding: 5px;
}
```
