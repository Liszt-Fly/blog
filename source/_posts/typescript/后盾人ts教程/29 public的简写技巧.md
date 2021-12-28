---
title: 29 public的简写技巧
categories:
  - typescript
  - 后盾人ts教程
---

当一个属性的权限修饰符为 public 的时候，可以不声明属性，直接在 constructor 内使用 public 修饰，自动设置为属性

```typescript
class User {
	constructor(public name: string) {
		this.name = name
	}
	public output() {
		console.log(this.name)
	}
}
new User("Mikeedu").output() //Mikeedu
```
