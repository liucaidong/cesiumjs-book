## Cesium.Primitive

基元表示几何中的几何[`Scene`](https://cesiumjs.org/Cesium/Build/Documentation/Scene.html)。的几何形状可以是从单一的[`GeometryInstance`](https://cesiumjs.org/Cesium/Build/Documentation/GeometryInstance.html)如实施例1所示的下方，或从实例的数组，即使几何形状是从不同的几何形状的类型

* 翻译：原始的，基元

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `geometryInstances` | Array。&lt;[GeometryInstance](https://cesiumjs.org/Cesium/Build/Documentation/GeometryInstance.html)&gt;\|[GeometryInstance](https://cesiumjs.org/Cesium/Build/Documentation/GeometryInstance.html) |  | 可选要呈现的几何实例（或单个几何实例）。 |
| `appearance` | [出现](https://cesiumjs.org/Cesium/Build/Documentation/Appearance.html) |  | 可选用于呈现基元的外观。 |
| `show` | 布尔 | `true` | optional确定是否显示此基元。 |
| `modelMatrix` | [Matrix4](https://cesiumjs.org/Cesium/Build/Documentation/Matrix4.html) | `Matrix4.IDENTITY` | 可选4x4变换矩阵，用于将基元（所有几何实例）从模型转换为世界坐标。 |
| `vertexCacheOptimize` | 布尔 | `false` | 可选时`true`，几何顶点针对前后顶点着色器缓存进行了优化。 |
| `interleave` | 布尔 | `false` | 可选时`true`，几何顶点属性是交错的，这可以略微提高渲染性能但会增加加载时间。 |
| `compressVertices` | 布尔 | `true` | 可选时`true`，压缩几何顶点，这将节省内存。 |
| `releaseGeometryInstances` | 布尔 | `true` | 可选时`true`，原语不保留对输入的引用`geometryInstances`以节省内存。 |
| `allowPicking` | 布尔 | `true` | 可选时`true`，每个几何实例只能选择[`Scene#pick`](https://cesiumjs.org/Cesium/Build/Documentation/Scene.html#pick)。当`false`，GPU内存被保存。 |
| `cull` | 布尔 | `true` | 可选时`true`，渲染器视锥体剔除和地平线根据其边界体积剔除图元的命令。`false`如果要手动剔除基元，请将此设置为小的性能增益。 |
| `asynchronous` | 布尔 | `true` | optional确定是初始化创建基元还是阻塞直到准备好。 |
| `debugShowBoundingVolume` | 布尔 | `false` | 可选仅用于调试。确定是否显示此基元的命令'边界球体。 |
| `shadows` | [ShadowMode](https://cesiumjs.org/Cesium/Build/Documentation/ShadowMode.html) | `ShadowMode.DISABLED` | optional确定此基元是否从每个光源投射或接收阴影。 |

#### 





