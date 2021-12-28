---
title: 6 for循环的执行原理
categories:
  - Javascript
  - 14 闭包和作用域
---

本节主要讨论异步执行，同步执行以及 var 和 let 的区别

## 同步执行

- var

```javascript
//在循环过程输入0,1,2,3
for (var i = 0; i <= 3; i++) {
	console.log(i)
}
console.log(i) //4;
```

- let

```javascript
//输出0,1,2,3
for (let m = 0; m <= 3; m++) {
	console.log(m)
}
//无法输出，不在全局变量中，不能进行输出
console.log(m)
```

## 异步执行

异步执行的关键是无论如何，同步部分的代码优先执行，而异步代码落后于同步代码执行

- var

```javascript
for (var i = 0; i <= 3; i++) {
	setTimeout(() => {
		console.log(i) //输出4个4
	}, 1000)
}
```

类似于开垦荒地，var 作用域决定了它不能开垦出新的地，自始自终都是对全局环境中 i 进行改变，当 i=4 的时候，不再进入循环，settimeout 函数一次性输出 4 个 4

- let

```javascript
for (let q = 0; q <= 3; q++) {
	setTimeout(() => {
		console.log(q)
	}, 1000)
}
```

let 具有块级作用域的性质，相当于 let 开垦了四块地，q 分别等于 0,1,2,3，然后在这四块地中执行 settimeout 函数

## 总结

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/image-20210722145539565.png)

- 对于 var 来说，首先生成了全局作用域，然后到 setTimeout，settimeout 是宏任务，添加到宏任务队列中，等全局的 i 一直叠加到 4 的时候，开始处理宏任务队列

* 对于 let 来说，每一次轮循的同时还会生成一个作用域，这个作用域中有 i 的值，然后也会有 setTimeout 的宏任务，当轮询执行完毕之后，每一个 setTimeout 都只会向上查找查找到对应的 i，所以输出 0，1，2，3
