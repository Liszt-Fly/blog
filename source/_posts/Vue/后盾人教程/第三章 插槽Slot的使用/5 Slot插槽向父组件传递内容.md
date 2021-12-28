---
title: 5 Slot插槽向父组件传递内容
categories:
  - vue
  - 插槽slot的使用
---

通过 Slot 插槽，也可以在子组件中传递内容，在父组件模版中使用

子组件

```html
<slot content="mikeedu" title="houdunren" :id="lesson.id" />
```

父组件
可以使用解构进行变量接收

```html
<template #default="{ content, title, id }">
	<button @click="del(id)">删除</button>
</template>
```
