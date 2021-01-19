# 学习笔记

## CSS

* `vertical-align`属性可以加在 inline, inline-block 或者 table-cell box 上。
* inline-block中`vertical-align`默认设置为baseline。
* `vertical-align: middle;`把元素放在父元素的中间。
* `line-height`可以指定text block的高度。
* CSS选择器：`.green .light`中间有空格，选择`.green`下面包含`.light`的元素。
* CSS选择器：`.green.light`中间没有空格，选择同时包含`.green`和`.light`的元素。



## JavaScript

* 条件运算符：

```javascript
// condition ? exprIfTrue : exprIfFalse
function example(…) {
    return condition1 ? value1
         : condition2 ? value2
         : condition3 ? value3
         : value4;
}
// 上下等价 
function example(…) {
    if (condition1) { return value1; }
    else if (condition2) { return value2; }
    else if (condition3) { return value3; }
    else { return value4; }
}
```

