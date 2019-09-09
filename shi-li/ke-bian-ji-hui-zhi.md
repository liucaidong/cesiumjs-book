## 可编辑绘制

##### 使用：

```
//化线
function drawLine() {
    viewer.scene.primitives.removeAll();
    var positionWord = [];
    positionWord.push(Cesium.Cartesian3.fromDegrees(110.20, 34.55, 0));
    positionWord.push(Cesium.Cartesian3.fromDegrees(115.20, 34.55, 0));
    positionWord.push(Cesium.Cartesian3.fromDegrees(115.20, 39.55, 0));
    //生成线
    var polyline = new ChangeablePrimitiveTool.PolylinePrimitive({
        positions: positionWord,
        width: 5,
        geodesic: true,
        objId: new Date().getTime() + 'id',
        //material: materialLine
    }, viewer);
    viewer.scene.primitives.add(polyline);
    polyline.setEditable();
    //添加监听事件
    polyline.addListener('onEdited', function (event) {
        var msg = '';
        if (event.objId) {
            msg = '编辑多段线,共' + event.positions.length + '个点-' + event.objId;
        } else {
            msg = '编辑多段线,共' + event.positions.length + '个点';
        }
        alert( msg);
    });
}
```



