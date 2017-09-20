# 第五章 原型

## 5.1[[Prototype]]

JavaScript中的对象有一个特殊的[[Prototypr]]内置属性，其实就是对其他对象的引用。几乎所有的对象在创建时[[Prototype]]属性都会被赋予一个非空的值。

### 5.1.1 Object.prototype

### 5.1.2 属性设置和屏蔽

```javascript
myObject.foo ='bar';
```

如果myObject对象中包含为foo的普通数据访问属性，这条赋值语句只会修改已有的属性值。

如果foo不是直接存在于myObject中，[[Prototype]]链就会被遍历，类似[[Get]]操作。如果原型链上找不到foo，foo就会被直接添加到myObject上。

如果属性么foo既出现在myObject中也出现在myObject的[[Prototype]]链上层，那么就会发生屏蔽。**myObject中包含的foo属性会屏蔽原型链上层的所有foo属性，因为myObject.foo总会选择原型链中最底层的foo的属性。**

屏蔽比我们想象中更加复杂。下面我们分析一下如果foo不直接存在于myObject中而是存在于原型链上层时myObject.foo=''bar''会出现三种情况。

1. 如果在[[Prototype]]链上层存在名为foo的普通数据访问属性并且没有被标记为只读（writable：false），那就会直接在myObject中添加一个名为foo的新属性，它是屏蔽属性。
2. 如果在[[Prototype]]链上层存在foo,但是它被标记为只读（writable：false），那么无法修改已有属性或者在myObject上创建屏蔽属性。如果运行在严格模式下，代码会抛出一个错误。否则，这条赋值语句会被忽略。总之，不会发生屏蔽。
3. 如果在[[Prototype]]链上层存在foo并且它是一个setter，那就一定会调用这个setter。foo不会被添加到（或者说屏蔽于）myObject，也不会重新定义foo这个setter。


