---
title: 34 abstract抽象类+方法
categories:
  - typescript
  - 后盾人ts教程
---

抽象类规定了一个笼统的规范，具体的实现可以不同，但是都要符合大体上的规范

**抽象类里可以没有抽象方法和抽象属性，但是抽象属性和方法所在类必须为抽象类**

```typescript
//Animation设置规范，规定需要有名称，移动方法，和获取位置方法
abstract class Animation {
	abstract name: string
	abstract move(): void
	protected getPos(): { x: number; y: number } {
		return { x: 100, y: 100 }
	}
}
//坦克实现Animation
class Tank extends Animation {
	name: string = "敌方坦克"
	public move(): void {
		console.log(`${this.name}移动`)
	}
}
//玩家实现Animation
class Player extends Animation {
	name: string = "我方坦克"
	public move(): void {
		console.log(`${this.name}移动`)
	}
}
```
