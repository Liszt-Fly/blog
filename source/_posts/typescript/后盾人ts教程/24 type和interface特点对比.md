---
title: 24 type 和 interface 特点对比
categories:
  - typescript
  - 后盾人ts教程
---

首先来看 type 和 interface 的定义

```typescript
//接口
interface Member {
	name: string
}
//type
type name = {
	name: string
}
```

## 共同点

type 和 interface 都可以被 class implements

```typescript
//interface
class Person implements User {
	age: number = 23
	name: string = "houdunren"
}
//type
class Person implements User {
	age: number = 23
	name: string = "houdunren"
}
```

type 和 interface 都可以互相继承 extends，但是语法稍有区别

- type extends type

```typescript
//type User Person
//interface Post Get
type User = User & Person
```

- type extends interface

```typescript
type = Post & User
```

- interface extends interface

```typescript
interface Post extends Get {}
```

- interface extends type

```typescript
interface Post extends Person {}
```

## 不同点

type 可以进行组合定义

```typescript
type name = {
	name: string
}
type age = {
	age: number
}
type User = name & age //name|age
```

type 可用于声明基本类型别名，联合类型

```typescript
type name = string
type Pet = dog | cat
type Pet = [dot, cat] //tuple类型
```

type 不支持重复声明

```typescript
type name = {
	name: string
}
//!error报错 type不允许重复声明
type name = {
	age: number
}
```

interface 可以重复声明，而且重复不会覆盖，而是叠加

```typescript
interface User {
	name: string
}
interface User {
	age: number
}
//这个时候的interface两个属性被叠加，相当于
interface User {
	name: string
	age: number
}
```
