---
layout: post
title: JavaScript
date: 2026-05-07 00:17:39 +0800
categories: [笔记]
---

JavaScript严格区分大小写，如果弄错了大小写，程序将报错或者运行不正常。


以`//`开头直到行末的字符被视为行注释，注释是给开发人员看到，JavaScript引擎会自动忽略：

```javascript
// 这是一行注释
alert('hello'); // 这也是注释
```

另一种块注释是用`/*...*/`把多行字符包裹起来，把一大“块”视为一个注释：
