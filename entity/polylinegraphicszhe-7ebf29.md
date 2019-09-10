## Cesium.PolylineGraphics

描述折线

| 姓名 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定折线的可见性。 |
| `positions` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定[`Cartesian3`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)定义线条的位置数组。 |
| `width` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | 可选数字属性，指定宽度（以像素为单位）。 |
| `granularity` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cesium.Math.RADIANS_PER_DEGREE` | 可选如果arcType不是ArcType.NONE，则指定每个纬度和经度之间的角距离的数字属性。 |
| `material` | [MaterialProperty](https://cesiumjs.org/Cesium/Build/Documentation/MaterialProperty.html) | `Color.WHITE` | optional一个属性，指定用于绘制折线的材质。 |
| `depthFailMaterial` | [MaterialProperty](https://cesiumjs.org/Cesium/Build/Documentation/MaterialProperty.html) |  | optional（可选）一个属性，指定在折线低于地形时用于绘制折线的材质。 |
| `arcType` | [弧光](https://cesiumjs.org/Cesium/Build/Documentation/ArcType.html) | `ArcType.GEODESIC` | 可选折线段必须遵循的线条类型。 |
| `clampToGround` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `false` | optional一个布尔属性，指定Polyline是否应该夹在地面上。 |
| `shadows` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ShadowMode.DISABLED` | optional枚举属性，指定折线是否投射或接收来自每个光源的阴影。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional（可选）一个属性，指定与此摄影线显示距离的距离。 |
| `classificationType` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ClassificationType.BOTH` | optional一个枚举属性，指定此折线是否会在地面上对terrain，3D Tiles或两者进行分类。 |
| `zIndex` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0` | optional一个属性，指定用于排序地面几何的zIndex。只有当\`clampToGround\`为真且支持地形上的折线时才有效。 |



