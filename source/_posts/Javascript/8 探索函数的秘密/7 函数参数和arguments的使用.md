---
title: 7 函数参数和arugments的使用
categories:
  - Javascript
  - 8 探索函数的秘密
---

arguments 是一个比较老的用法，在 function 中使用代表函数中的参数

```javascript
function test(a, b, c, d) {
	console.log(arguments)
}
test("a", "b", "c", "d")
```

可以看出所有的参数都显示在了 arguments 中
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/2s1hko.png)

使用 arguments 来计算 total 值

```javascript
function sum() {
	let total = 0
	for (let i = 0; i < arguments.length; i++) {
		total += arguments[i]
	}
	return total
}
```
