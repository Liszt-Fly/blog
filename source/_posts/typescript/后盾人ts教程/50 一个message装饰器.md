---
title: 50 一个message装饰器
categories:
  - typescript
  - 后盾人ts教程
---

我们将装饰器中添加参数，根据 class 不同，装饰器中输出不同的内容

比如我们可以定义一个 message 装饰器,对于不同的类输出不同的消息

```typescript
const MessageDecorator = (target: Function) => {
	target.prototype.message = (content: string) => {
		console.log(content)
	}
}
@MessageDecorator
class LoginController {
	public login() {
		console.log("登陆业务处理")
		;(<any>this).message("恭喜你，登陆成功")
	}
}
@MessageDecorator
class ArticleController {
	public store() {
		;(<any>this).message("添加文章成功")
	}
}

new LoginController().login()
```
