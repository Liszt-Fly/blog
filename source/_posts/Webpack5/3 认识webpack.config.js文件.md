---
title: 3 认识webpack.config.js文件
categories:
  - Webpack5
---

webpack 中有许多的配置项，虽然很多都有默认的配置项，但是不一定适用于所有的场景，我们需要在`webpack.config.js`文件中进行修改

让我们来看看它的项目解构和最基本的配置吧!

```javascript
const path = require("path")
module.exports = {
	//指定入口
	entry: "./src/index.js",
	//输出文件
	output: {
		//输出文件的文件名
		filename: "bundle.js",
		//输出文件的存放路径
		path: path.resolve(__dirname, "./output"),
	},
}
```
