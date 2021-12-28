---
title: 9 批量设置props技巧
categories:
  - Vue
  - Vue3.0组件化开发
---

使用`v-bind`可以批量设置 Props,让我们来看一个例子

```html
<hd-button
	id="test"
	v-bind="{ content: '保存', type: 'success', hdTip: '@' }"
></hd-button>
```
