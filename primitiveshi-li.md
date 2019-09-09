#### 实例

```
//声明几何体实例
var instance = new Cesium.GeometryInstance({
  //几何体
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



