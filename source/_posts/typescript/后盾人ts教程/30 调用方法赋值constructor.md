---
title: 30 调用方法赋值constructor
categories:
  - typescript
  - 后盾人ts教程
---

对 constructor 赋值，除了赋值给上形参，也可以调用方法，将方法的返回值作为传输

```typescript
class User {
	consturctor(public name: string) {
		this.name = this.initName("name")
	}
	private initName(name: string): string {
		return `${name}-houdunren.com`
	}
}

const hd = new User("houdunren")
console.log(hd.name) //name-houdunren.com
```
