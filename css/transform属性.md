# transform属性

这是css3的属性。这篇主要涉及到rotate(*angle*)，其中*angle*是旋转的具体角度

```
div{
    transform:rotate(7deg);
    -ms-transform:rotate(7deg); 	/* IE 9 */
    -moz-transform:rotate(7deg); 	/* Firefox */
    -webkit-transform:rotate(7deg); /* Safari 和 Chrome */
    -o-transform:rotate(7deg); 	/* Opera */
}
```

**提示**：

*Internet Explorer 10、Firefox、Opera 支持 transform 属性。*

*Internet Explorer 9 支持替代的 -ms-transform 属性（仅适用于 2D 转换）。*

*Safari 和 Chrome 支持替代的 -webkit-transform 属性（3D 和 2D 转换）。*

*Opera 只支持 2D 转换。*



在js中取值或者赋值时，要这样

```
//取值
var deg = document.getElementById("id").style.transform || document.getElementById("id").style.webkitTransform || document.getElementById("id").style.msTransform || document.getElementById("id").style.oTransform || document.getElementById("id").style.mozTransform;
//赋值
document.getElementById("id").style.transform = deg; 
document.getElementById("id").style.webkitTransform = deg; 
document.getElementById("id").style.msTransform = deg; 
document.getElementById("id").style.oTransform = deg; 
document.getElementById("id").style.mozTransform = deg; 
```

