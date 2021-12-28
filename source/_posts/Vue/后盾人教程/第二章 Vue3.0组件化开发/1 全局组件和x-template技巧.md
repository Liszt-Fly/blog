---
title: 1 全局组件和x-template技巧
categories:
  - Vue
  - Vue3.0组件化开发
---

首先要注意，关于组件的命名，尽量使用短横线的形式
比如

```javascript
component: hdButton
```

```html
<hd-button></hd-button>
```

## 全局组件

<font color='#ea8685'>特别注意，component 的注册顺序不影响使用，即便组件在后面定义，前面的组件也可以使用</font>

```javascript
//根组件
const app = Vue.createApp({
	template: `<div>向军 <hd-xj/></div>`,
})
//子组件 也是全局组件
app.component("hdXj", {
	template: `<div>向军大叔-<hd/></div>`,
})
```

## x-template 的使用

x-template 就是一个 template 模版，内容写到了 x-template 中

```html
<script type="text/x-template" id="hdTemplate">
	<h2>后盾人-JS教学</h2>
</script>
```

在 JS 中使用 x-template 定义的内容

```javascript
app.component("hd", {
	template: `#hdTemplate`,
})
```
