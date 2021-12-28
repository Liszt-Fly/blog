---
title: 3 let,const,var
categories:
  - Javascript
  - 1 步入Javascript黑洞
---

常见的块级作用域

- 函数体 函数体内自成一个作用域
- {}
- module 一个 module 是一个独立的作用域
- for 循环 这个循环也是一个作用域

## var

var 出现在早期，它不具备很多新的性质，也有非常多的弊端，并不建议使用 var,但需要对 var 有一定了解

- var 可以重复进行声明

```javascript
var a = 1
var a = 2
console.log(a)
```

- var 不具有块级作用域

```javascript
{
	var a = 1
} //块级作用域
console.log(a) //1
```

{}是一组块级作用域，但是由于 a 不支持块级作用域的性质，在块外部也能进行访问

在块级作用域中我们说明了 var 声明的变量是可以穿透 for 循环的

```javascript
var i = 99
for (var i = 0; i < 5; i++) {
	//var 没有块作用域
	console.log(i)
}
console.log(i) //5
```

可以看出，在经历了这个循环之后，循环外部的 i 值也被修改为了 5，而不再是原来的 99

- 变量提升 var 声明的变量支持变量提升

- var 声明的变量都押入了 window 对象中

## let

let 是更完美的 var 变量，是 var 的升级版本

- let 拥有更健壮的块级作用域

```javascript
{
	let age = 10
}
console.log(age) //不属于同一个作用域，无法进行访问
```

再看一下刚才的 for 循环例子

```javascript
let m = 99
for (let m = 0; m < 5; m++) {
	//let具有块作用域
	console.log(m)
}
console.log(m) //99
```

在循环内部定义了 m ，循环完成之后 m 的输出值为 99 ，并非是 5

- let 必须先声明后使用，否则会形成 TDC 暂时性死区

```javascript
console.log(web) //Can not access "web" before initialization
let web = "houdunren"
```

- let 不可以重复进行声明

- let 声明的变量不会压入 windows

## const

const 具有 let 所有的特性，但是 const 声明的变量不可变

对于不可变性我们需要分成两类来讨论，一类是值类型变量，另一类是引用类型

### 值类型

```javascript
const a = 1
a = 2 //报错
```

### 引用类型

```javascript
const b = { age: 5 }
b.age = 10
console.log(b.age) //10
```

有人或许会说 b 发生变化了，可是实际上并没有变化，引用类型使用 const 关心的是地址，这个地址不发生变化，那么就是没有变化，我们可以看出这些变化都是内部的值发生了变化

## let,const,var 的共同点

- 函数中可以访问到外面的全局变量
  意思是函数作用域链自下而上，内部肯定能访问外部的，但是外部不能访问内部的

```javascript
var web = "houdunren.com"
function show() {
	console.log(web)
}
show() //houdunren.com
console.log(web) //houdunren.com
```

- 私有领域有定义优先使用私有领域的定义

```javascript
var value = 1
function get() {
	//私有领域定义的话就采用私有领域
	var value = 3
	console.log(value)
}
get() //3
console.log(value) //1
```

let 代码同理
