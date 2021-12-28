---
title: v-show vs v-if
categories:
  - Vue
  - 后盾人教程
  - 第一章 Vue基础入门
---

v-show 和 v-if 都能控制元素的显示或者隐藏，对于 v-show 来说，使用 display:none 进行隐藏，而对于 v-if 来说为 false 的时候不渲染该 DOM 元素

:accept:对于频繁切换显示隐藏状态的元素，建议使用 v-show，性能开销更小

