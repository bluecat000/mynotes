---
title: 解析赋值
layout: post
---

对象的左右数量无关
需要重命名的使用符号`:`(import,export用`as`)  不需要的化只需要传入变量

```javascript
let {a,b,c: admin,d,f} = {
  a() {
    console.log(1)
  },
  b() {
    console.log(2)
  },
  c() {
    console.log(3)
  },
  d: 1,
}

var obj = {
  a,b,admin,d,f
}

// or
// {
//  ...arr
// }

console.log(obj)

```
