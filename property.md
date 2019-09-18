# PolylineDashMaterialProperty

一个MaterialProperty映射到折线破折号Material制服的。

#### 实例

```
var dashedLine = viewer.entities.add({
    name : 'Blue dashed line',
    polyline : {
        positions : Cesium.Cartesian3.fromDegreesArrayHeights([-75, 45, 500000,
                                                               -125, 45, 500000]),
        width : 4,
        //虚线
        material : new Cesium.PolylineDashMaterialProperty({
            color: Cesium.Color.CYAN
        })
    }
});

```



