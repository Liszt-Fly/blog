---
title: 9 void与never的用法
categories:
  - typescript
  - 后盾人ts教程
---

void 与 never 基本上都是用于函数返回值之中，但二者之间有细微的区别

## void

void 多用于函数的返回值

```typescript
function run(): string | void {
	console.log("Hello,World!")
}
```

## never

never 不会执行到结束，用于抛出错误的函数

```typescript
function handle(): never {
	throw new Error("类型错误")
}
```
