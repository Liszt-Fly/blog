---
title: 27 class继承权限修改
categories:
  - typescript
  - 后盾人ts教程
---

经过类继承权限可以进行修改，但对于 private,protected,private 情况不同

- 父类是 private,子类必须维持 private，不能修改权限

* 父类是 protected，子类可以维持 protected 或者升级为 public

* 父类是 public，子类只能维持 public

简单总结，权限修改只能向上兼容，private->protected->public 按照这个顺序进行权限的调整
