---
title: 11 css样式继承与隔离
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

在 vue 中，如果启用 scoped 关键字,该组件的样式将会隔离，不会作用到子组件

```html
<style scoped></style>
```

但是如果不启用 scoped 关键字，父组件样式会作用到子组件

## class/style 传递

父组件

```html
<class-inline-vue class="xj"></class-inline-vue>
```

子组件

```css
.xj {
	background-color: green;
	color: white;
}
```

```html
<template>
	<div>help</div>
	<!--使用$attrs.class将属性压入子属性-->
	<div :class="$attrs.class">another</div>
	<div :style="[{ backgroundColor: 'orange', color: 'white' }, hdStyle]">
		级联样式
	</div>
</template>
```

结果如下，class 并没有传递给所有组件，而是具有`$attrs.class`属性的子组件

![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/5aGSIt.png)
