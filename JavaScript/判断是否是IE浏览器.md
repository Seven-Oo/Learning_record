# 判断是否是IE浏览器

```
var userAgent = navigator.userAgent // 取得浏览器的userAgent字符串
var isIE = userAgent.indexOf('compatible') > -1 && userAgent.indexOf('MSIE') > -1 // 判断是否IE<11浏览器
if(isIE){
    console.log("IE")
    return true
}else {
    console.log("Not IE")
    return false
}

//ie11 edge
var isIE = (!!window.ActiveXObject || 'ActiveXObject' in window)
```

