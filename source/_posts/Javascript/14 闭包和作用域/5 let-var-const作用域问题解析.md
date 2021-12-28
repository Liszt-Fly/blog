---
title: 5 let-var作用域问题解析
categories:
  - Javascript
  - 14 闭包和作用域
---

## let

let 具有块作用域的机制

```javascript
{
	let a = 1
}
{
	let a = 2
}
```

## var

var 不具有块作用域的机制，并且 var 变量存在于全局作用域中，可以使用 window 访问

```javascript
{
	var a = 1
	var b = 2
}
console.log(window.b) //2;
```

## const

const 具有块级作用域

```javascript
{
	const a = 1
}
{
	const a = 1
}
```
