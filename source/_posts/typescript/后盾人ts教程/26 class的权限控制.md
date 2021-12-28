---
title: 26 class的权限控制
categories:
  - typescript
  - 后盾人ts教程
---

三种权限修饰符: Public,Private,Protected

- Public: 都可以进行访问
- Protected:只允许类内部和继承该类的子类进行访问
- Private:只允许在类的内部进行访问

## Public

```typescript
class User {
	public age: number
	public name: string
	constructor(n: string, a: number) {
		this.name = n
		this.age = a
	}
}
//new一个对象
const hd = new User("Mike", 21)
console.log(hd.age) //在外部正常访问
console.log(hd.name) //在外部正常访问
```

## Protected

```typescript
class User {
	protected age: number
	protected name: string
	constructor(n: string, a: number) {
		this.name = n
		this.age = a
	}
	public info() {
		console.log(`${this.name}的年龄是${this.age}`) //在class内部可以访问到protected的变量
	}
	protected getInfo() {} //在class内部可以访问到protected的变量
}
class SuperUser extends User {
	constructor(n: string, a: number) {
		super(n, a)
	}
	public show() {
		this.getInfo() //可以调用父类的getInfo方法
	}
}

new User("houdunren", 24).getInfo() //error
```

## Private

```typescript
class User {
	protected age: number
	protected name: string
	constructor(n: string, a: number) {
		this.name = n
		this.age = a
	}
	public info() {
		console.log(`${this.name}的年龄是${this.age}`)
	}
	private getInfo() {} //在class内部可以访问到private的方法
}
class SuperUser extends User {
	constructor(n: string, a: number) {
		super(n, a)
	}
	public show() {
		this.getInfo() //子类无法调用父类的private方法
	}
}
new User("houdunren", 24).getInfo() //外部也无法调用private方法
```
