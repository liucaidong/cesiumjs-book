#### pickEllipsoid {#pickEllipsoid}

选择一个椭圆体或地图

* -&gt; Cartesian3

|  |
| :--- |


| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `windowPosition` | [Cartesian2](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html) |  | 像素的x和y坐标。 |
| `ellipsoid` | [椭球](https://cesiumjs.org/Cesium/Build/Documentation/Ellipsoid.html) | `Ellipsoid.WGS84` | 可选要选择的椭圆体。 |
| `result` | [Cartesian3](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html) |  | optional要存储结果的对象。 |

##### 返回：

如果选择了椭圆体或贴图，则返回椭圆体或地图表面上世界坐标中的**点**。

如果未选择椭圆体或贴图，则返回undefined。

