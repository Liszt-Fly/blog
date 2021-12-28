---
title: 43 泛型在class中的使用
categories:
  - typescript
  - 后盾人ts教程
---

```typescript
class User<T> {
	public constructor(private _user: T)
	public get(): T {
		return this._user
	}
}
interface UserInterface {
	name: string
	age: number
}

const obj = new User<UserInterface>({ name: "mikeedu", age: 18 })
console.log(obj.get().name) //mikeedu
```
