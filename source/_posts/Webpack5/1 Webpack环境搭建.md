---
title: 1 Webpack环境搭建
categories:
  - Webpack5
---

## 什么是 webpack?

我们在学习 webpack 之前首先要了解什么是 webpack
webpack 官网的图已经很明显的告诉了我们
![alt](https://mikes.oss-cn-beijing.aliyuncs.com/uPic/FhxLjS.png)
webpack 将 js 文件，图片资源，css-processor(css 预处理器),css 等其他资源打包成静态模块
🧰 定义:本质上，webpack 是一个用于现代 JavaScript 应用程序的静态模块打包工具，webpack 的核心是 <span style='background-color:#d35400;color:#ddd;padding:0 5px 0 5px'>模块化</span>

🧷 总的来说，webpack 的两大功能

- 模块化，webpack 采用了先进化模块化管理

* 打包机，webpack 是一个模块打包机，它将 js，以及浏览器本身不能处理的资源文件(css,less,png,jpg)通过合适的 loader 进行打包处理，从而让浏览器可以正常访问

## 项目基本环境搭建

创建新的项目

```bash
npm init --y
```

安装 webpack 的核心依赖

```bash
npm install webpack webpack-cli
```

> webpack-cli 是什么? webpack-cli 是使用 webpack 的命令行工具，在 4.x 版本之后不再作为 webpack 的依赖了，我们使用时需要单独安装这个工具

新建`src`文件夹，用于存放 js 脚本

到这步为止，我们的项目构建就基本完成了
