## Cesium.Primitive

基元表示几何中的几何[`Scene`](https://cesiumjs.org/Cesium/Build/Documentation/Scene.html)。的几何形状可以是从单一的[`GeometryInstance`](https://cesiumjs.org/Cesium/Build/Documentation/GeometryInstance.html)如实施例1所示的下方，或从实例的数组，即使几何形状是从不同的几何形状的类型

* 翻译：原始的，基元

#### 实例

```
//声明几何体实例
var instance = new Cesium.GeometryInstance({
  geometry : new Cesium.EllipseGeometry({
      center : Cesium.Cartesian3.fromDegrees(-100.0, 20.0),
      semiMinorAxis : 500000.0,
      semiMajorAxis : 1000000.0,
      rotation : Cesium.Math.PI_OVER_FOUR,
      vertexFormat : Cesium.VertexFormat.POSITION_AND_ST
  }),
  id : 'object returned when this instance is picked and to get/set per-instance attributes'
});
//添加到场景的几何体中
scene.primitives.add(new Cesium.Primitive({
  //几何实例
  geometryInstances : instance,
  appearance : new Cesium.EllipsoidSurfaceAppearance({
    material : Cesium.Material.fromType('Checkerboard')
  })
}));
```



