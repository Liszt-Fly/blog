---
title: 37 接口在class中的使用
categories:
  - typescript
  - 后盾人ts教程
---

```typescript
{
	interface userInterface {
		name: string
		age: number
	}
	//类中使用interface
	class User {
		private _info: userInterface
		constructor(user: userInterface) {
			this._info = user
		}
		get info(): userInterface {
			return this._info
		}
	}
	const hd = new User({ name: "Mike", age: 18 })
	console.log(hd.info)
}
```
