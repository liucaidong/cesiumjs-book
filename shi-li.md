## 画线

使用：

```
viewer.scene.primitives.removeAll();
var positionWord = [];
positionWord.push(Cesium.Cartesian3.fromDegrees(110.20, 34.55, 0));
positionWord.push(Cesium.Cartesian3.fromDegrees(105.20, 34.55, 0));
positionWord.push(Cesium.Cartesian3.fromDegrees(105.20, 39.55, 0));
var polygon = new ChangeablePrimitiveTool.PolygonPrimitive({
    positions: positionWord,
    objId: new Date().getTime() + 'id',
},viewer);
viewer.scene.primitives.add(polygon);
polygon.setEditable();
polygon.addListener('onEdited', function (event) {
    var lonlatArr = [];
    for (var i = 0; i < event.positions.length; i++) {
        var cartographic = Cesium.Cartographic.fromCartesian(event.positions[i]);
        var lonlat = [Cesium.Math.toDegrees(cartographic.longitude), Cesium.Math.toDegrees(cartographic.latitude)];
        lonlatArr.push(lonlat);
    }
    var msg = '';
    if (event.objId) {
        msg = '编辑多段线,共' + lonlatArr.length + '个点-' + event.objId;
    } else {
        msg = '编辑多段线,共' + lonlatArr.length + '个点';
    }
    alert(msg);
});
```

tool 代码：

```

```



