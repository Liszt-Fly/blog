---
title: 13 typescript中的点语法
categories:
  - typescript
  - 后盾人ts教程
---

使用 js 中学习点语法最常用的数字求和例子

```typescript
function sum(...args: number[]) {
	return args.reduce((s, n) => s + n, 0)
}
console.log(sum(1, 2, 3, 4, 5, 6))
```
