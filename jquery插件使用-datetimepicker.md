# datetimppicker插件的使用

使用场景:

表单控件太丑，且显示格式不适合，所以可以采用日历控件。

基本使用

这个插件应该属于jquery插件的分支，所以可以去jquery插件库查找。

文件名称如下

jquery.datetimepicker.css

jquery.datetimepicker.js

将两个文件导入

example

```html
<input  id='begin_date' placeholder="请选择开始时间"  readonly>
```

注意： readonly是input属性，意思是只能读取，如果不这样的，input可以被用户填写。

js:

```javascript
var init = function() {
        $('#begin_date').datetimepicker({
            lang: "ch",  //语言
            yearStart: 2016, //最小念想，实际测试好像没什么乱用
            format:"Y-m-d",	//填写到input的日期格式
            yearEnd: 2030,  //最大念想
            timepicker: false,
            scrollInput:false,
            onClose: function() {
                viewModel.begin_date( $('#begin_date').val() );
            } //将在日历空间的选取的日期复制给input
        });
```