# 绑定-控制流-with绑定

with绑定创建了一个新的绑定上下文，这样，子元素就被绑定到某个特定对象的上下文中了。

example

```html
<h1 data-bind="text: city"></h1>
<p data-bind="with: coords">
	Latitude: <span data-bind="text: latitude"></span>
  	Longitude: <span data-bind=s"text: logitude"></span>
</p>
<script type="text/javascript">
	ko.applyBindings({
      city:"London",
      coords: {
        latitude: 51,
        logitude: -0.126
      }
	})
</script>
```



