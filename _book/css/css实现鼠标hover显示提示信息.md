# css实现鼠标hover显示提示信息

```
你需要定义的选择器:hover:after {
    position: absolute;
    left: 15px;
    top: 5px;
    padding: 5px;
    background-color: #0095ff;
    border-radius: 5px;
    color: #fff;
    /*这里显示的内容为提示信息*/
    content: ‘你好，这是通过css实现的信息展示’;
    z-index: 2;
    width: 120px;
}
```

