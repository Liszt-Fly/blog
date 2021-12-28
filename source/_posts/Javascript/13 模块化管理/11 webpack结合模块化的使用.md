---
title: 11 webpack结合模块化的使用
categories:
  - Javascript
  - 13 模块化管理
---

首先创建项目文件夹，然后使用 `npm init -y` 对项目进行初始化，然后安装 webpack 相关项

```bash
npm i webpack webpack-cli --save-dev
```

在 `package.json` 中添加 dev 开发项命令

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "dev": "webpack --mode development --watch"
  },
```

我们创建一个 style.js 模块，该模块的作用是改变网页的颜色

```javascript
export default class Style {
	constructor() {}
	init() {
		document.body.style.backgroundColor = "red"
	}
}
```

在项目的 `index.js` 文件中引入

```javascript
import Style from "./style"
new Style().init()
```

在 bash 中使用命令打包，然后在 dist 文件夹可以发现生成的 main.js 文件

```bash
npm run dev
```

在 `index.html` 文件中进行引入

```html
<script src="dist/main.js"></script>
```

可以发现生成的网页是红色，并且改变 `style.js`代码中的颜色，网页中的颜色也会随即刷新
