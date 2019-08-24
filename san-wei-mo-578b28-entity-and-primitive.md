# -三维模型\(Entity&Primitive\)

#### \#Entity

简明使用

1. viewer.entities.add

**例子**

```
//添加entity
viewer.entities.add({
    position: Cesium.Cartesian3.fromDegrees(homePOsition[0], homePOsition[1]),
    point: {
        pixelSize: 10,
        color: Cesium.Color.YELLOW
    }
});
```

具体创建什么模型，和设置的属性看官网API

#### \#primitve

简明使用

1. 声明 new Cesium.GeometryInstance\( { geometry : new Cesium.RectangleGeometry } \)

2. 添加viewer.scene.primitives.add

外观设置

1. 声明new Cesium.PerInstanceColorAppearance
2. 使用{appearance ： }

**例子**

```
//声明对象实例
var instance = new Cesium.GeometryInstance({
    geometry: new Cesium.RectangleGeometry({
        rectangle: Cesium.Rectangle.fromDegrees(105.20, 30.55, 106.20, 31.55),
        vertexFormat:Cesium.EllipsoidSurfaceAppearance.VERTEXT_FORMAT
    }),
    id: 'rectangle-1',
});
//将实例添加到地图
viewer.scene.primitives.add(new Cesium.Primitive({
    geometryInstances: instance,
    appearance: new Cesium.EllipsoidSurfaceAppearance({ //外观设置
        material:Cesium.Material.fromType('Stripe')
    })
}));
```

添加多个则 perimitives.add -&gt; geometryInstances : \[\]\(存放实例组\)

#### \#事件

地图事件使用处理程序：new Cesium.ScreenSpaceEventHandler\(\);



