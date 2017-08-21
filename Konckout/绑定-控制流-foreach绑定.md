# 绑定-控制流-foreach绑定

foreach绑定会为了一个数组的每个条目复制一个标记片段，然后将该标注的每个拷贝分别绑定到对应的数组元素上。一般用来渲染list或table非常有用。

example

```html
 <table>
        <thead>
        <tr><th>First name</th><th>Last name</th></tr>
        </thead>
        <tbody data-bind="foreach: people">
            <tr>
                <td data-bind="text: firstName"></td>
                <td data-bind="text: lastName"></td>
            </tr>
        </tbody>
    </table>
    <script type="text/javascript">
        ko.applyBindings({
            people: [
                {firstName: 'Bert',lastName:'Bertington'},
                {firstName: 'CHarles',lastName:'CHarlesforth'}
            ]
        })
    </script>
```

注意：用$data 引入每个数组条目(元素)

如果你想引入数组条目自身（不是它的某个属性）该怎么做？在这种情况下，你可以使用特殊的上下文属性$data。在foreach代码块之内，它指的是”当前项目“