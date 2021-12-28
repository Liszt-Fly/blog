---
title: 11 event验证参数传递
categories:
  - Vue
  - Vue3.0组件化开发
---

可以对 event 传递的参数进行验证，如果不符合要求，可以在控制台中弹出 warning 进行警告

在上一节中我们的 emits 形式是`emits:[]`数组形式，但是如果要启用验证，我们就需要使用`emits:{}`

```javascript
emits:{
    //表示add事件不需要进行参数验证
        add:null,
    	del(v) {
			if (/^\d+$/.test(v)) {
				return true
			}
			console.error("del emit需要数值参数")
		},
}
```
