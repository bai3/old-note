# Computed Observables

computed能够绑定多个依赖，当这些依赖中的任何一个发生变化时，它们会自动更新

example

js:

```javascript
function AppViewModel(){
	this.firstName = ko.observable('Bob');
	this.lastName = ko.observable('Smith');
  	this.fullName = ko.computed(function(){
      return this.firstName()+""+this.lastName();
  	},this)
}
```

```html
<span data-bind="text: firstName"></span>
<span data-bind="text: lastName"></span>
<span data-bind="text: fullName"></span>
```

## 管理‘this’

一种流行的、将问题简化的惯例

有一种流行的惯例，能够完全避免追踪this：如果你的视图模型的构造函数将this的引用拷贝到一个不同的变量中(通常叫做self),那么你就可以在你的视图模型中通篇地使用self，而不用担心它被重新定义，指向其他东西。

```javascript
function AppViewModel(){
  var self = this;
  self.firstName = ko.observable('Bob')
}
```

由于self是该函数的闭包中被捕获的，它可以再任何嵌套的函数之中使用，比如computed observable的求值函数。





