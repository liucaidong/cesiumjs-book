# PolygonGraphics

描述由构成外部形状和任何嵌套孔的线性环的层次结构定义的多边形。

多边形符合地球的曲率，可以放置在地面上或海拔高度，并且可以选择性地挤压成一个体积。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定多边形的可见性。 |
| `hierarchy` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个指定的属性[`PolygonHierarchy`](https://cesiumjs.org/Cesium/Build/Documentation/PolygonHierarchy.html)。 |
| `height` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0` | optional一个数字属性，指定多边形相对于椭球面的高度。 |
| `heightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定高度相对于什么。 |
| `extrudedHeight` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个数字属性，指定多边形的挤压面相对于椭球面的高度。 |
| `extrudedHeightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定extrudedHeight相对于什么。 |
| `stRotation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | optional一个数字属性，指定从北向逆时针旋转多边形纹理。 |
| `granularity` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cesium.Math.RADIANS_PER_DEGREE` | optional一个数字属性，指定每个纬度和经度点之间的角度距离。 |
| `fill` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定是否使用提供的材质填充多边形。 |
| `material` | [MaterialProperty](https://cesiumjs.org/Cesium/Build/Documentation/MaterialProperty.html) | `Color.WHITE` | optional一个属性，指定用于填充多边形的材质。 |
| `outline` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `false` | optional一个boolean属性，指定是否概述多边形。 |
| `outlineColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.BLACK` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)轮廓的属性。 |
| `outlineWidth` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个指定轮廓宽度的数字属性。 |
| `perPositionHeight` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `false` | optional一个布尔值，指定是否使用每个位置的高度。 |
| `closeTop` | 布尔 | `true` | 可选如果为false，则从展开的挤出多边形顶部开始。 |
| `closeBottom` | 布尔 | `true` | 可选如果为false，则将拉出多边形的底部打开。 |
| `arcType` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ArcType.GEODESIC` | 可选多边形边必须遵循的线条类型。 |
| `shadows` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ShadowMode.DISABLED` | optional枚举属性，指定多边形是否从每个光源投射或接收阴影。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional（可选）一个属性，指定与相机的距离，以显示此多边形。 |
| `classificationType` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ClassificationType.BOTH` | optional一个枚举属性，指定此多边形是否会在地面上对terrain，3D Tiles或两者进行分类。 |
| `zIndex` | [ConstantProperty](https://cesiumjs.org/Cesium/Build/Documentation/ConstantProperty.html) | `0` | optional一个属性，指定用于排序地面几何的zIndex。仅在多边形为常量且未指定height或extrudedHeight时才有效。 |

##### 例子：

```
viewer.entities.add({
    name : 'Red polygon on surface',
    polygon : {
        hierarchy : Cesium.Cartesian3.fromDegreesArray([-115.0, 37.0,
                                                        -115.0, 32.0,
                                                        -107.0, 33.0,
                                                        -102.0, 31.0,
                                                        -102.0, 35.0]),
        material : Cesium.Color.RED
    }
});
```



