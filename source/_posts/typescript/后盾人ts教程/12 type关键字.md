---
title: 12 type关键字
categories:
  - typescript
  - 后盾人ts教程
---

type 定义是为了重复使用某些会反复用到的类型
比如添加用户，更新用户，用户都是由名字，年龄组成的，性别对于用户是一个可选项，用户选择性提供，我们就可以提供一个 user 的用户类型

```typescript
type user = {
	name: string
	age: number
	sex?: string | number
}
//添加用户方法
let addUser = (user: user): void => {
	console.log("添加用户")
}
//更新用户
let updateUser = (user: user): void => {
	console.log("更新用户")
}

addUser({ name: "后盾人", age: 21, sex: "男" })
updateUser({ name: "Mike", age: 22 })
```
