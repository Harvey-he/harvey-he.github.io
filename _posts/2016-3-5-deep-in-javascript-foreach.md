---
layout: post
title: "深入了解JavaScript数组和对象的循环遍历"
categories:
- javaScript
tags:
- 深入了解JavaScript
---

## 前言

写这篇文章的意义，一者想让自己对JavaScript的循环遍历有一个深入的了解，二者也是在工作中经常用到，发现并没有深入了解过不同遍历方法的异同。于是决定写这篇文章，以敦促自己总结；

下面分开两个大版本的JavaScript和分别俩个小点（数组和对象的循环遍历），来阐释JavaScript中遇到的循环遍历

## ES5

ES5为目前最通用的JavaScript语言版本，浏览器支持最广泛，可以说是现行标准。

### 数组（Array）

数组的循环遍历方法较多，单在ES5的标准下，就有三种遍历方法。

#### for循环

需使用数组的`length`属性，结合for循环来遍历数组

```js
var a = [1, 2, 3];
for ( var i = 0; i < a.length; i++) {
  var value = a[i];
  console.log(value);
}
// 1
// 2
// 3
```

#### for...in循环

`for...in`遍历也可以遍历数组的所有元素，需要注意的是`for...in`遍历的是数组的所有键值

```js
var a = [1, 2, 3];
for (var key in a) {
  console.log('key:' + key);
  var value = a[key];
  console.log('value:' + value);
}

// key:0
// value:1
// key:1
// value:2
// key:2
// value:3
```

#### forEach方法

`forEach`方法遍历数组，相比前两种方法，更加全面，可以认为是前两种方法的结合体，`forEach`方法遍历后回调方法里，会返回是三个参数。

第一个`currentValue`，当前遍历到的数组元素
第二个`index`，当前遍历到的数组元素的键值
第三个`array`，数组本身

```js
var a = [1, 2, 3];

a.forEach(function functionName(value, key, array) {
  console.log('key:' + key);
  var value = a[key];
  console.log('value:' + value);
  console.log('array:' + array);
});
// key:0
// value:1
// array:1,2,3
// key:1
// value:2
// array:1,2,3
// key:2
// value:3
// array:1,2,3
```

此方法详见：[forEach方法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

### 对象（Object）

## ES6

### 数组（Array）

### 对象（Object）

未完待续。。。
