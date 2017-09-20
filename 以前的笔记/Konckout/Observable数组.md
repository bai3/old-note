# Observable数组

如果你想要探测某个对象的变化，并对之作出反应，你可以使用observable。如果你想要探测一组事物的变化，并对之作出反应，那么使用observableArray。

example：

```javascript
var myObservableArray = ko.observableArray();
myObservableArray.push('Some  value')
```

要点：一个observableArray的操作并不会让该对象的属性自身变成observable。当然，你可以Iran过这些属性变成observable的，如果你想这么做的话，但是这是依赖选项。一个observableArray只追踪它持有哪些对象，当添加或删除对象时，它会通知监听器。

## 从一个observableArray读取信息

example：

```javascript
alert('The length of the array is'+myObservableArray().length);
alert('The first element is'+myObservableArray()[0]);
```

从技术角度来说，你可以使用任何原生的JavaScript数组的函数，来操作这个底层的数组，但是，正常情况下，有更好的代替办法。KO的observableArray自己有对等的函数，它们更有用。

- 它们都能在目标浏览器上运行
- 对于修改数组内容的那些函数而言，比如push和spilce注释*(spilce()方法向数组中添加或删除项目，然后返回被删除的项目。)*KO的对应方法会自动地触发依赖追踪机制，以便所有被注册过的监听器能够收到相关变化的通知，这样，你的UI也会自动更新。
- 其语法更加方便，要想调用KO的push方法，值需要编写myObservableArray.push(...)。这种做法比通过myObservableArray().push(...)来调用底层数组的push方法稍微好一点

## 读取observableArray数组信息

- indexOf函数返回数组中第一个和你的参数匹配的项目的索引。
- slice函数是observableArray实现和原生JavaScript slice对等的方法，它返回数组中”从某个开始索引凐某个结束索引“之间的项目。

## 操作一个observableArray

observableArray暴露一组类似的函数，用于修改数组的内容并通知监听器。

- pop
- push
- shift
- unshift
- reverse
- sort
- splice

remove 和 removeAll

- myObservableArray.remove(someItem)删除所有等于someItem的值，并将它们作为一个数组返回
- myObservableArray,remove(function(item{ return item.age < 18}))删除所有age属性小于18的值，并将它们作为一个数组返回
- myObservableArray.removeAll()删除所有值，并将它们作为一个数组返回。