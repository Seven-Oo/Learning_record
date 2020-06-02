# 将获取到的transform矩阵值转换为deg

方法函数：

```
function getmatrix(a,b,c,d){
    var aa=Math.round(180*Math.asin(a)/ Math.PI);
    var bb=Math.round(180*Math.acos(b)/ Math.PI);
    var cc=Math.round(180*Math.asin(c)/ Math.PI);
    var dd=Math.round(180*Math.acos(d)/ Math.PI);
    var deg=0;
    if(aa==bb||-aa==bb){
        deg=dd;
    }else if(-aa+bb==180){
        deg=180+cc;
    }else if(aa+bb==180){
        deg=360-cc||360-dd;
    }
    return deg>=360?0:deg;
    //return (aa+','+bb+','+cc+','+dd);
}
```

具体使用：

```
var transform = 获取元素的transform值；
var values = transform.split('(')[1].split(')')[0].split(',');
var a = values[0];
var b = values[1];
var c = values[2];
var d = values[3];

transform = getmatrix(a,b,c,d);//将矩阵转换为deg
```

另一种方法：

```
var el = document.getElementById("divTransform");
var st = window.getComputedStyle(el, null);
var tr = st.getPropertyValue("-webkit-transform") ||
    st.getPropertyValue("-moz-transform") ||
    st.getPropertyValue("-ms-transform") ||
    st.getPropertyValue("-o-transform") ||
    st.getPropertyValue("transform") ||
    "FAIL";
// With rotate(30deg)...
// matrix(0.866025, 0.5, -0.5, 0.866025, 0px, 0px)
console.log('Matrix: ' + tr);
// rotation matrix - http://en.wikipedia.org/wiki/Rotation_matrix
var values = tr.split('(')[1].split(')')[0].split(',');
var a = values[0];
var b = values[1];
var c = values[2];
var d = values[3];
var scale = Math.sqrt(a * a + b * b);
console.log('Scale: ' + scale);
// arc sin, convert from radians to degrees, round
var sin = b / scale;
// next line works for 30deg but not 130deg (returns 50);
// var angle = Math.round(Math.asin(sin) * (180/Math.PI));
var angle = Math.round(Math.atan2(b, a) * (180 / Math.PI));
console.log('Rotate: ' + angle + 'deg');
```

但是 这个方法中的 270度显示为 -90度