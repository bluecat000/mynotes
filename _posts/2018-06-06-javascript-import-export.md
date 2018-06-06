---
title: javascript中的import export
layout: post
---

es6用于模块的输出和导入，使得js可以进行模块化开发

- 静态加载，输出一个接口除了default之外不能直接输出变量
- 输出的是静态引用，使用的时候去export的环境中获取值，所以输出的值可以变动 (CMD不同)，值的改变只能在输出模块中改变，环境外改变无效
- 不可以放在代码块中(如if)
- 自动使用`严格模式`

## 模块`export.js`
```javascript
let val = 1000
function fn () {
  console.log('fn')
}

export {
  val,
  fn
}

export const c = 1

export default 1

setTimeout(() {
  val = 100
}, 1000)

```


## 常用加载方法`import.js`
```javascript

import * as m from './export.js'
m.default
m.fn()
m.val

// or

import {fn as func, val} from './export.js'
func()
setTimeout(() {
  console.log(val) // 100
})

// or

import def from './export.js'
console.log(def) // 1

```

## 复合写法`mergeImport.js`
```javascript
export {fn, a} from './export.js'
```

## 使用import()动态加载
```javascript
if(true) {
  import('./export.js')
    .then((m) {
      m.default
      m.fn
    })
    .catch((err) => {})
  // or
  import('./export.js')
    .then(({fn,val as value}) {
      fn()
      value
    })
    .catch((err) => {})
}
```

- 返回promise 回调函数包含整个module，和`import \*`一样
- 动态加载，可以放入代码块中
- 支持动态路径`import(fn())`

