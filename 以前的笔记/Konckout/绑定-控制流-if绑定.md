# 绑定-控制流-if绑定

只有当某个指定的表达式求值之后等于true（或者类true，比如非null对象或非空字符串），if绑定让一个标记片段出现在你的页面文档中（使用它的dat-bind属性）

if扮演着类似visible绑定的角色。区别是，使用visible绑定的话，所包含的标记总是保留在DOM元素中，并总会应用其data-bind属性-visible绑定只是使用CSS来反转容器元素的可见性。然而，if绑定，会实际地添加或删除你的DOM中所包含的标记，只当表达式为true，才将绑定应用到子元素上。

example

```html
<label><input type="checkbox" data-bind="checkd
  :displayMessage">Display message</label>
<div>
  Here is a message.Astonishing
</div>
```

```javascript
ko.applyBindings({
  	displayMessage: ko.observable(false)
})
```

