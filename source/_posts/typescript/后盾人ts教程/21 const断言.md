---
title: 21 const断言
categories:
  - typescript
  - 后盾人ts教程
---

## 基本使用

在 20 中说明了可以使用值约束，使用 <span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>as const</span>可以完成

```typescript
let m = "mike" as const //等同于 let m:"mike"
```

## 数组使用

使用 <span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>as const</span>可以将数组转化为元组(tuple)，并且类型约束->值约束

```typescript
let arr = [5, "hello", 23] //类型约束为 number|string
//使用as const关键字转化为元组,
let arr = [5, "hello", 23] //[5,"hello",23]
```

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/5u5Y7P.png)

⚡ **特别注意** 数组为值和数组为变量的区别

- 数组内为值 转化为值类型限定的元组
- 数组内为变量 转化为类型限定形式的元组

```typescript
let a = 1
let b = 2
let arr = [a, b] as const //[numer,number]

let arr1 = [1, 2] as const //[1,2]
```

还可以结合泛型使用

```typescript
let hd = <const>[a5, a6]
```

## 对象使用

对于对象来说，传递值还是变量没有区别，都是值锁定

```typescript
//name只能取houdunren 值锁定
const obj={
    name:"houdunren
}

//name只能取houdunren 值锁定
let name="houdunren
const obj={
    name:name
}
```

## 解构中使用

为什么要使用？比如解构出来的一个是值，一个是函数 Function，返回的函数是数组形式，如果使用函数接收，数组变量的类型约束为 <span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>string|Function</span>,我们无法确认哪一个是值哪一个是函数，调用就会引起报错。

解决方案:使用 as const 将数组转化为元组，一一对应

```typescript
//解构中使用as const
function hdcms() {
	let a = "hello,world"
	let b: Function = () => {
		console.log("THIS")
	}
	return [a, b] as const
}

const [ar, sr] = hdcms()
sr() //无法确定哪一个是Function,只有使用as const 进行确定
```
