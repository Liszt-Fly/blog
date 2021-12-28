---
title: 7 template模版
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

`<template></template>`和`<div></div>`是相似的，但是 div 是具有样式的容器，而 template 仅仅是一个承载逻辑的容器，并无样式

```javascript
	data() {
				return {
					lessons: [
						{
							name: "如何学好C++",
							price: 100,
						},
						{
							name: "javascript精粹",
							price: 125,
						},
						{
							name: "mysql入门",
							price: 250,
						},
					],
				}
			},
```

```html
<template v-for=" lesson in lessons">
	{{lesson.name}}-{{lesson.price}}
</template>
```

可以看出并没有容器容纳，仅仅执行了 v-for 的逻辑
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/uVDBA0.png)
