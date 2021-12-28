---
title: '8 any,unknown,as用法'
categories:
  - typescript
  - 后盾人ts教程
---

## any

any 的作用让 typescript 丧失类型校验的特性，any 代表的是任何类型都可以，如果使用太多的 any 会失去使用 typescript 的意义
这同 javascript 没有任何区别

```typescript
let a: any = 3
a = "hello"
a = false
```

## unknown

unknown 需要和 any 区分开来，unknown 只是类型未知，但它是具有类型的

```typescript
let xj: unknown = "houdunren"
let g: string = xj //type unknown is not assigable to string
```

虽然我们明知道 xj 变量是 <span style='background-color:#d35400;color:#ddd'>string</span> 类型，但是仍然不能进行赋值
使用 as 关键字进行转换

```typescript
let g: string = xj as string
```

## as

as 的用法已经在 unknown 中体现了
除此之外，还有另一种使用方法:比如我们需要把字符串转化为数字,直接 string as number 是不可行的，这时候使用 unknown 进行一次中转就可以顺利完成转换

```typescript
let q: string = "99"
let q1: number = q as unknown as number
console.log(q1) //99
```
