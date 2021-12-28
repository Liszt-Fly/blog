---
title: 4 Props按钮组件
categories:
  - Vue
  - Vue3.0组件化开发
---

## Props 组件创建

本节使用创建自定义 button 的案例来讲解 props 的作用
Button 是各式各样的，我们如果希望对按钮的内容，样式进行定制化，使用 props 是一个不错的选择

props 让我们可以在父组件向子组件传递内容，从而控制子组件
app.component

```html
<template>
	<hd-button content="INFO" type="info"></hd-button>
	<hd-button content="Danger" type="danger"></hd-button>
	<hd-button content="warning" type="warning"></hd-button>
</template>
```

hdButton.component

在 template 中，我们规定了按钮的内容以及 class 类型使用父组件传递的 props 内容，从而达到了组件自定义化的目的

```html
<template>
	<div :class="['hd-button', type]">{{ content }}</div>
</template>
```

在 js 中使用 props，规定传递内容的类型约束
注意类型约束使用的是构造函数 String,Function,Number...，甚至可以使用自定义的构造函数来进行限制约束

```javascript
<script>
export default {
	props: {
		content: String,
		type: String,
	},
}
</script>
```

css

```css
.hd-button {
	width: 100px;
	height: 40px;
	background-color: #1abc9c;
	color: white;
	display: flex;
	align-items: center;
	justify-content: center;
	cursor: pointer;
	user-select: none;
	margin-bottom: 20px;
}
.info {
	background-color: #bdc3c7;
	color: black;
}
.danger {
	background-color: #e74c3c;
}
.warning {
	background-color: #f39c12;
}
```

## props 的更多设置

我们可以对 props 的结构稍作修改，设置更多的内容，如默认值，required 属性以及 validator 验证属性

```javascript
props: {
	type: {
		type: String,
        default:"success",
        required:true,
        validator(v){
            return ["success","info","danger"].includes(v)
        }
	}
}
```
