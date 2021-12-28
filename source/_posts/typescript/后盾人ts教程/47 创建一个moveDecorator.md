---
title: 47 类装饰器
categories:
  - typescript
  - 后盾人ts教程
---

Example:现在有一个 Tank 类，我们提供一个 moveDecorator 的装饰类，从 prototype 上提供一个 getPosition 的方法，返回坦克的位置信息

```typescript
//decorator
	const moveDecorator: ClassDecorator = (target: Function) => {
		target.prototype.getPosition = (x: number, y: number) => {
			return { x: 100, y: 200 }
		}

//声明坦克类
@moveDecorator
class Tank{}
console.log((<any>t).getPosition())
const t = new Tank()
```
