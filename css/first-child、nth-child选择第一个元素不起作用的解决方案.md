# first-child、nth-child(1)选择第一个元素不起作用的解决方案

看下面结构的代码：

```
<div class="user-info-container">
	<div class="user-avatar-box"><img src="" alt="" /></div>
	<div class="user-info-item name"><p>姓名：</p><p>xxx</p><div>
	<div class="user-info-item age"><p>年龄：</p><p>30</p><div>
	<div class="user-info-item nation"><p>民族：</p><p>汉族</p><div>
	<div class="user-info-item occupation"><p>职业：</p><p>前端工程师</p><div>
</div>
```

这时

```
.user-info-item {
	margin-top: 30px;
}
.user-info-item:first-child {
	margin-top: 15px;
}
```

或者

```
.user-info-item:nth-child(1) {
	margin-top: 15px;
}
```

都不能将class为 user-info-item name 的margin-top设置为15px；这是为什么呢？查询具体属性后知道了原因，这是因为：



![](E:\May\vscodeProject\Learing Record\Learning_record\_book\gitbook\images\first-child.png)



![](E:\May\vscodeProject\Learing Record\Learning_record\_book\gitbook\images\nth-child.png)



图中可以看出，这两个选择器都是选取其父元素下的首个/第n个子元素，然后再判断这个元素是不是伪类调用者，如果是就运用{}里的属性，不是的话就不运用

所以在这里，它选取的其实是

```
<div class="user-avatar-box"><img src="" alt="" /></div>
```

但这个元素并不匹配相应的class，所以不运用该样式。这里如果想要运用该样式，需要修改

```
.user-info-item:nth-child(2) {
	margin-top: 15px;
}
```

或者使用first-child，就需要修改页面结构

```
<div class="user-info-container">
	<div class="user-avatar-box"><img src="" alt="" /></div>
	<div class="user-info-itemWrapper">
		<div class="user-info-item name"><p>姓名：</p><p>xxx</p><div>
		<div class="user-info-item age"><p>年龄：</p><p>30</p><div>
		<div class="user-info-item nation"><p>民族：</p><p>汉族</p><div>
		<div class="user-info-item occupation"><p>职业：</p><p>前端工程师</p><div>
	</div>
</div>
```

为class为 user-info-item 的所有元素添加一个父级<div class="user-info-itemWrapper">



------

下面要介绍两个新的选择器：:nth-of-type() 和 :first-of-type

很明显了 “first-of-type" 一定是和”第一“有关——:first-of-type 选择器匹配元素其父级是特定类型的第一个子元素。

**提示:** 和 :nth-of-type(1) 是一个意思。

而，:nth-of-type(n)选择器匹配同类型中的第n个同级兄弟元素。

看例子

```
<div>
    <h1>这是标题</h1>
    <p>这是第一个段落。</p>
    <p>这是第二个段落。</p>
    <p>这是第三个段落。</p>
    <p>这是第四个段落。</p>
</div>
```

那么在这段代码中，想要设置第一个p标签的背景为红色的话，需要

```
p:first-of-type {
	background: red;
}
```

或者

```
p:nth-of-type(1) {
	background: red;
}
```

