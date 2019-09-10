## PolylineGeometry

折线建模为线条的描述; 前两个位置定义一个线段

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `positions` | 数组。&lt;[Cartesian3](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)&gt; |  | [`Cartesian3`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)将折线中的位置定义为线条的数组。 |
| `width` | 数 | `1.0` | 可选以像素为单位的宽度。 |
| `colors` | 数组。&lt;[颜色](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)&gt; |  | optional一个[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)定义每个顶点或每个段颜色的数组。 |
| `colorsPerVertex` | 布尔 | `false` | optional一个布尔值，用于确定颜色在线的每个线段上是平的还是在顶点之间插值。 |
| `arcType` | [弧光](https://cesiumjs.org/Cesium/Build/Documentation/ArcType.html) | `ArcType.GEODESIC` | 可选折线段必须遵循的线条类型。 |
| `granularity` | 数 | `CesiumMath.RADIANS_PER_DEGREE` | 可选如果options.arcType不是ArcType.NONE，则每个纬度和经度之间的距离（以弧度表示）。确定缓冲区中的位置数。 |
| `vertexFormat` | [VertexFormat](https://cesiumjs.org/Cesium/Build/Documentation/VertexFormat.html) | `VertexFormat.DEFAULT` | 可选要计算的顶点属性。 |
| `ellipsoid` | [椭球](https://cesiumjs.org/Cesium/Build/Documentation/Ellipsoid.html) | `Ellipsoid.WGS84` | 可选用作参考的椭圆体。 |



