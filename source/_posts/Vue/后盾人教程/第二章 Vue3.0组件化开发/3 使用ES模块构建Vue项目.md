---
title: 3 使用ES模块构建Vue项目
categories:
  - Vue
  - Vue3.0组件化开发
---

首先使用 tree 命令看看项目的结构
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/kK6NNC.png)

项目由 App.js(JS 模块),todo.js 数据模块，index.html(视图模块)组成

index.html

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<title>Document</title>
		<script src="https://unpkg.com/vue@next"></script>
	</head>
	<body>
		<div id="app">
			<div v-for="data in db"><todo :data="data" /></div>
		</div>
		<script type="module">
			//核心步骤，导入模块
			import App from "./App.js"
		</script>
	</body>
</html>
```

todo.js
todo.js 作用于提供数据

```javascript
export default [
	{ id: 1, title: "该项目的质量非常高" },
	{ id: 2, title: "今晚一起去吃饭" },
]
```

component/todo.js

```javascript
export default {
	props: ["data"],
	data() {
		return {
			content: "todo",
		}
	},
	template: `<div style="background-color:#1abc9c;color:#fff;margin-bottom:30px;padding:10px;">{{data.title}}</div>`,
}
```
