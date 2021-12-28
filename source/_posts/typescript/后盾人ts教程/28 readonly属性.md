---
title: 28 readonly属性
categories:
  - typescript
  - 后盾人ts教程
---

readonly 属性顾名思义，就是只读属性，不允许修改

```typescript
class Axios {
	readonly site: string = "https://qiaoyangedu.top"
}
const instace = new Axios()
instace.site = "houdunren.com" //error readonly属性不可以修改
```

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/ZzdBGI.png)

但是 readoly 属性并不是真的不可修改，在 constructor 初始化的时候是可以进行修改的

```typescript
class Axios {
	readonly site: string = "https://qiaoyangedu.com"
	public constructor(site?: string) {
		this.site = site || "https://houdunren.com"
	}
	public get(url: string): any[] {
		console.log(`你请求的是${this.site}/${url}`)
		return []
	}
}

const instance1 = new Axios("https://houdunren.com")
console.log(instance1.get("about")) //你请求的是https://houdunren.com/about
```
