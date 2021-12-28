---
title: 3 TS的特点
categories:
  - typescript
  - 后盾人ts教程
---

## 类型校验

类型校验是 typescript 的特点之一
在 JavaScript 中，一个变量的类型可以进行更改

### 隐式校验

```javascript
let a = 1
a = "hello,world"
a = true
```

在 typescript 中，变量在声明的时候类型就进行确定，不能随意更改

变量 Example

```typescript
let a = 1
a = "hello,world" //typescript中报错
//错误信息：Type 'string' is not assignable to type 'number'
```

数组 Example

```typescript
const hd1 = ["houdunren.com"]
hd1.push("yahoo.com")
//* hd1.push(3)
//报错，number类型不能赋值给string类型
const hd2 = ["houdunren.com", 2]
hd2.push(4)
hd2.push("hello")
```

除了隐式（implicit）检查，TS 还提供了类型注解的方式进行校验

### 类型注解

```typescript
let a: string
a = "hello" //👌
a = 3 //🚫
```

对函数进行注解

```typescript
function sum(a: number, b: number): number {
	return a + b
}
console.log(sum(5, 3))
```

## 强大的智能提示

由于 TS 具有静态类型，所以可以提供强大的智能提示
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/D2SeFA.png)
