---
title: 31 class的静态属性和方法
categories:
  - typescript
  - 后盾人ts教程
---

静态属性和方法相比于普通属性和方法，最大的特点就是：静态属性和方法属于类的，不属于实例的，而普通属性和方法是属于实例的。**静态方法由类调用，而普通方法由实例调用**

```typescript
class Axios {
	static site: string = "houdunren.com"
	static getSite(): string {
		return Axios.site
	}
}
console.log(Axios.site) //静态属性属于类
console.log(Axios.getSite()) //静态方法由类调用
const instance = new Axios() //在实例上找不到site属性和getSite方法
```
