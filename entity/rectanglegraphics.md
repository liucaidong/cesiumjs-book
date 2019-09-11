## Cesium.RectangleGraphics

描述a的图形矩形符合地球的曲率，可以放置在地面上或海拔高度，并可以选择性地挤压成一个体积。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定矩形的可见性。 |
| `coordinates` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选属性指定[`Rectangle`](https://cesiumjs.org/Cesium/Build/Documentation/Rectangle.html)。 |
| `height` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0` | optional一个数字属性，指定矩形相对于椭球面的高度。 |
| `heightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定高度相对于什么。 |
| `extrudedHeight` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个数字属性，指定矩形的挤压面相对于椭球面的高度。 |
| `extrudedHeightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定extrudedHeight相对于什么。 |
| `rotation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | optional一个数字属性，指定从北向顺时针旋转矩形。 |
| `stRotation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | optional一个数字属性，指定从北向逆时针旋转矩形纹理。 |
| `granularity` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cesium.Math.RADIANS_PER_DEGREE` | optional一个数字属性，指定矩形上各点之间的角距离。 |
| `fill` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定矩形是否填充了提供的材质。 |
| `material` | [MaterialProperty](https://cesiumjs.org/Cesium/Build/Documentation/MaterialProperty.html) | `Color.WHITE` | optional一个属性，指定用于填充矩形的材质。 |
| `outline` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `false` | optional一个布尔属性，指定矩形是否已轮廓化。 |
| `outlineColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.BLACK` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)轮廓的属性。 |
| `outlineWidth` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个指定轮廓宽度的数字属性。 |
| `shadows` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ShadowMode.DISABLED` | optional枚举属性，指定矩形是否从每个光源投射或接收阴影。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定与相机相距该显示矩形的距离。 |
| `classificationType` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ClassificationType.BOTH` | optional一个枚举属性，指定此矩形是否会在地面上对terrain，3D Tiles或两者进行分类。 |
| `zIndex` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0` | optional一个属性，指定用于排序地面几何的zIndex。仅当矩形是常量且未指定height或extrudedHeight时才有效。 |

##### 实例

```
var redRectangle = viewer.entities.add({
    name : 'Red translucent rectangle',
    rectangle : {
        coordinates : Cesium.Rectangle.fromDegrees(-110.0, 20.0, -80.0, 25.0),
        material : Cesium.Color.RED.withAlpha(0.5)
    }
});
```



