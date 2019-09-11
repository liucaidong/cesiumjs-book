# EllipseGraphics

```
new Cesium.EllipseGraphics(options)
```

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定椭圆的可见性。 |
| `semiMajorAxis` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional指定半长轴的数字属性。 |
| `semiMinorAxis` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional指定半短轴的数字属性。 |
| `height` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0` | optional一个数字属性，指定椭圆相对于椭球面的高度。 |
| `heightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定高度相对于什么。 |
| `extrudedHeight` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个数字属性，指定椭圆的挤压面相对于椭球面的高度。 |
| `extrudedHeightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定extrudedHeight相对于什么。 |
| `rotation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | optional一个数字属性，指定椭圆从北向逆时针旋转。 |
| `stRotation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | optional一个数字属性，指定从北向逆时针旋转椭圆纹理。 |
| `granularity` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cesium.Math.RADIANS_PER_DEGREE` | optional一个数字属性，指定椭圆上点之间的角距离。 |
| `fill` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定椭圆是否使用提供的材质填充。 |
| `material` | [MaterialProperty](https://cesiumjs.org/Cesium/Build/Documentation/MaterialProperty.html) | `Color.WHITE` | optional一个属性，指定用于填充椭圆的材质。 |
| `outline` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `false` | optional一个boolean属性，指定椭圆是否被轮廓化。 |
| `outlineColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.BLACK` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)轮廓的属性。 |
| `outlineWidth` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个指定轮廓宽度的数字属性。 |
| `numberOfVerticalLines` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `16` | optional一个数字属性，指定沿轮廓周边绘制的垂直线数。 |
| `shadows` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ShadowMode.DISABLED` | optional枚举属性，指定椭圆是否从每个光源投射或接收阴影。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定与摄像机相距该椭圆的距离。 |
| `classificationType` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ClassificationType.BOTH` | optional一个枚举属性，指定此椭圆是否会在地面上对terrain，3D Tiles或两者进行分类。 |
| `zIndex` | [ConstantProperty](https://cesiumjs.org/Cesium/Build/Documentation/ConstantProperty.html) | `0` | optional一个指定Ellipse的zIndex的属性。用于订购地面几何形状。仅在椭圆为常量且未指定height或exturdedHeight时才有效。 |



