# css渐变写法，兼容IE

在css3之前想要做背景色渐变的效果，就只能采用背景图片的方法。但是随着css3中 **linear-gradient** 属性的出现，就可以避免使用背景图片的方法，从而优化了性能。

但是 **linear-gradient** 的属性在IE9以下是无效的，但还可以采用IE滤镜的方法。

比如：黑色到白色的渐变

```
.gradient {
	background: -moz-linear-gradient(top, #000 0%, #fff 100%);
	background: -webkit-linear-gradient(linear, left top, left bottom, color-stop(0%, #000), color-stop(100%, #fff));
	background: -webkit-linear-gradient(top, #000 0%, #fff 100%);
	background: -o-linear-gradient(top, #000 0%, #fff 100%);
	background: -ms-linear-gradient(top, #000 0%, #fff 100%);
	background: linear-gradient(to bottom, #000 0%, #fff 100%);
}
```

IE滤镜：filter

linear-gradient在IE9以下是不支持的，所以针对  IE6-IE8  我们需要使用滤镜

```
.gradient {
	filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#000', endColorstr='#fff', GradientType=0);
}
```

由于 **filter** 是IE的私有属性，所以我们需要针对IE9单独处理滤镜效果

```
:root {filter: none;}
```

最后的兼容写法如下

```
.gradient{ 
    background: #000000; 
    background: -moz-linear-gradient(top, #000000 0%, #ffffff 100%); 
    background: -webkit-gradient(linear, left top, left bottom, color-stop(0%,#000000), color-stop(100%,#ffffff)); 
    background: -webkit-linear-gradient(top, #000000 0%,#ffffff 100%); 
    background: -o-linear-gradient(top, #000000 0%,#ffffff 100%); 
    background: -ms-linear-gradient(top, #000000 0%,#ffffff 100%); 
    background: linear-gradient(to bottom, #000000 0%,#ffffff 100%); 
    filter: progid:DXImageTransform.Microsoft.gradient( startColorstr='#000000', endColorstr='#ffffff',GradientType=0 ); 
} 
:root .gradient{filter:none;} 
```

