# 利用observables创建view models

## Observables

Konckout基于下面三个核心功能特征：

- Observables 和依赖追踪

- 声明时绑定

- 使用模板


## MVVM和视图模型

Model-View-View Model（MVVM）是一种用于构建用户界面的设计模式。它描述了如何可能会变复杂的UI保持简单，通过将其分为三部分来做到：

- 模型:你的应用程序所存储的数据。该数据代表了你的业务领域中的各种对象和操作（比如可以进行汇款的银行账号），该数据和UI无关。当使用KO的时候，你通常会对一些服务器端代码进行Ajax调用，用于读写这个被存储的模型数据。

- 视图模型（view model）:该数据及其操作在UI的一种纯代码表述。比如，如果你正在实现一个列表编辑器，你的view model将会是一个对象，它包含了一列项目，并且暴露了用于添加和删除这些项目的方法。

- 视图（view）:可见的、交互式的UI，展现了视图模型的状态。它显示了来自视图模型的信息，将命令发送给视图模型，它随着视图模型的状态改变而更新。

  当使用KO的时候，你的视图就是你的HTML文档，它带有声明式绑定，用于将它的视图模型关联起来。



创建一个带有KO的视图模型，比如

```javascript
var myViewModel = {
  personName: 'Bob',
  personAge: 123
}
```

然后就可以进行声明式绑定，即为该视图模型创建一个非常简单的视图

```html
The name is <span data-bind="text: personName"></span>
```

## 激活Knockout

data-bind属性不是HTMl原生属性，所以要激活Knockout

```javascript
ko.applyBindings(myViewModel)
```

ko.applybindings的参数含义

- 第一个参数是说，你要想将”什么样的视图模型对象“用于它要激活的”交互式绑定“
- 你可以传入第二个参数，用于定义”你想要在该文档哪一部分“搜索data-bind属性，这是可选的。比如，ko。applyBindings(myViewModel,document.getElementById('someElementId'))。这就将激活动作限制在ID为someElementId的元素及其子元素上；如果你有多个视图模型，并且每个视图模型都关联了该页面的不同区域，那么这么做就会很有用。

## Observables

KO的主要好处之一是当视图模型发生变化时，它会自动更新你的UI。

你可以将你的视图模型的属性声明为observables，因为这些属性是特殊的JavaScript对象，它们可以将变化通知给subscribers，并能够自动地检测依赖对象。

example：

```javascript
var myViewModel = {
  personName： ko.observable('BOb'),
  personAge: ko.observable(123)
}
```

现在绑定能够探测到变化，当它探测到变化时，它就会自动地更新视图。

## observables的读/写

ko.observables实际上是函数

- 读取observable的当前值，只需调用该observable，不要传入参数。
- 写一个新值到该observable，那么调用该observable，将新值作为一个参数传入。
- 要想将多个值写入一个模型对象的多个observable属性中，你可以使用链式语法，比如，myViewModel.personName('Mary').personAge(50)会将name的值修改为’Mary‘,并且将age的值修改为50.

