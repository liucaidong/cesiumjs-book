## Cesium.GeometryInstance

几何实例允许一个[`Geometry`](https://cesiumjs.org/Cesium/Build/Documentation/Geometry.html)对象在几个不同位置中的位置并且唯一地着色

* 翻译：几何实例

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `geometry` | [几何](https://cesiumjs.org/Cesium/Build/Documentation/Geometry.html) |  | 实例的几何。 |
| `modelMatrix` | [Matrix4](https://cesiumjs.org/Cesium/Build/Documentation/Matrix4.html) | `Matrix4.IDENTITY` | 可选模型矩阵，用于转换以将几何图形从模型转换为世界坐标。 |
| `id` | 宾语 |  | optional一个用户定义的对象，在选择实例时返回，[`Scene#pick`](https://cesiumjs.org/Cesium/Build/Documentation/Scene.html#pick)或者使用每个实例属性获取/设置[`Primitive#getGeometryInstanceAttributes`](https://cesiumjs.org/Cesium/Build/Documentation/Primitive.html#getGeometryInstanceAttributes)。 |
| `attributes` | 宾语 |  | 可选的Per-instance属性，如下面示例中显示的show或color属性。 |

#### 



