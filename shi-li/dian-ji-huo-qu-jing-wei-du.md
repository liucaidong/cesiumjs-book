## 点击获取经纬度

```
 mouseHandlerDraw.setInputAction(function (movement) {
      var cartesian = scene.camera.pickEllipsoid(movement.position, ellipsoid);
      var cartographic = Cesium.Cartographic.fromCartesian(cartesian)；
      //经纬度
      var lonlat = [Cesium.Math.toDegrees(cartographic.longitude), Cesium.Math.toDegrees(cartographic.latitude)];
 }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
```

鼠标移动： movement.endPosition

