---
title: 2 typescript 环境配置
categories:
  - typescript
  - 后盾人ts教程
---

## TS 安装

首先需要全局安装 typescript

```Bash
brew install typescript
```

并使用命令验证是否安装成功

```Bash
tsc -v
```

采用的编辑器是 vscode,由于 vscode 和 typescript 都是微软推出，在 vscode 编辑器中 typescript 可以得到很好的支持

## 关闭 js 校验

不希望 ts 编译生成的 js 文件也进行同样的校验，需要在 vscode 的 settings 中取消对 javascript 验证的勾选
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/Visi9o.png)

## 生成 js 文件

使用 tsc 将 ts 文件编译为 ts 文件

```Bash
tsc Filename.ts
```

如果 ts 文件修改，希望 js 文件也进行修改

```Bash
tsc Filename.ts -w
```

出现该消息表示监听成功，按 control+c 即可停止监听
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/zVwVpy.png)
