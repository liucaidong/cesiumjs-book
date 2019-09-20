# EllipsoidGeodesic

在连接两个提供的行星点的椭球上初始化测地线。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |


| `start` | [制图](https://cesiumjs.org/Cesium/Build/Documentation/Cartographic.html) |  | 可选路径上的初始行星点。 |
| :--- | :--- | :--- | :--- |


| `end` | [制图](https://cesiumjs.org/Cesium/Build/Documentation/Cartographic.html) |  | 可选路径上的最终行星点。 |
| :--- | :--- | :--- | :--- |


| `ellipsoid` | [椭球](https://cesiumjs.org/Cesium/Build/Documentation/Ellipsoid.html) | `Ellipsoid.WGS84` | 可选的测地线所在的椭圆体。 |
| :--- | :--- | :--- | :--- |


#### 属性

#### surfaceDistance {#surfaceDistance}

获取起点和终点之间的表面距离

```
//获取两点之间的距离
geodesic.setEndPoints(startCartographic, endCartographic);
var lengthInMeters = Math.round(geodesic.surfaceDistance);
```

#### 方法

#### interpolateUsingFraction（fraction，result） {#interpolateUsingFraction}

提供沿测地线指示部分的点的位置。

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| `fraction` | 数 | 初始点和最终点之间距离的一部分。 |
| `result` | [制图](https://cesiumjs.org/Cesium/Build/Documentation/Cartographic.html) | 存储结果的对象。 |

返回：

沿着测地线的点的位置。

```
//实例：获得两点之间的中点位置
var scratch = new Cesium.Cartographic();
var geodesic = new Cesium.EllipsoidGeodesic();
geodesic.setEndPoints(startCartographic, endCartographic);
var midpointCartographic = geodesic.interpolateUsingFraction(0.5, scratch);
return Cesium.Cartesian3.fromRadians(midpointCartographic.longitude, midpointCartographic.latitude);
```



