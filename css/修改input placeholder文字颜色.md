# 修改input placeholder文字颜色

修改所有的input

```
::-webkit-input-placeholder {
	color: red
}
::-moz-placeholder {/* Firefox 19+ */
	color: red
}
:-moz-placeholder {/* Firefox 18- */
	color: red
}
:-ms-input-placeholder {
	color: red
}
```

修改某个标签

```
#myInput::-webkit-input-placeholder,
#myInput::-moz-placeholder,
#myInput:-ms-input-placeholder {
	color: red
}
```

