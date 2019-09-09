## 实现线

* 点的操作

执行：参数： viewer,lineoption,callback

```
function drawLine() {
    var lineOption = {
        width: 5,
        geodesic: true
    };
    DynamicDrawTool.startDrawingPolyshape(viewer, false, lineOption, function (cartesians) {
        //下面对处理代码
        //....
    });
}
```

动态绘制工具

```
var DynamicDrawTool = (function(){
    
});
```

* 线的实现



