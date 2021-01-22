# 学习笔记

## Proxy 用法

```javascript
let obj = {
    a: 1,
    b: 2
}
// 最普通的Object，不可observe

let po = new Proxy(object, {
    set(obj, prop, val) {
        console.log(obj, prop, val);
    } // 当设置对象的值时，触发set函数
})
// Proxy对象，当触发一些hook时会触发一些函数
// po相当于obj的一个代理，如果在po中改变obj，那么obj也会改变
```

* 双向绑定：
    * 当DOM元素属性改变时，JS中对象属性改变，（通过`addEventListener()`实现）
    * 当JS中对象属性改变时，DOM元素属性也改变，（通过`Proxy`实现：`Proxy`对象属性改变 --> 触发`Proxy`中的`set`方法 --> `set`方法设置JS对象属性的同时，触发`callback`函数，改变DOM中元素属性）

## JavaScript Map 用法

```javascript
let contacts = new Map()
contacts.set('Jessie', {phone: "213-555-1234", address: "123 N 1st Ave"})
contacts.has('Jessie') // true
contacts.get('Hilary') // undefined
contacts.set('Hilary', {phone: "617-555-4321", address: "321 S 2nd St"})
contacts.get('Jessie') // {phone: "213-555-1234", address: "123 N 1st Ave"}
contacts.delete('Raymond') // false
contacts.delete('Jessie') // true
console.log(contacts.size) // 1
```



## CSSOM-Range

```javascript
let range = document.createRange(); // 创建一个range
range.setStart(startNode, startOffset); // startOffset为从startNode开始偏移的字符长度
range.setEnd(endNode, endOffset);
range.getBoundingClientRect(); //返回一个DOMRect对象，包含x,y,宽高等信息
range.insertNode(newNode); // 在range起始位置插入一个node
```

* `range`本身只记录`startNode`和相对于`startNode`的offset，只有当调用`range.getBoundingClientRect()`时才会返回具体`range`的位置信息。