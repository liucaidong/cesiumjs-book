## getPickRay\(windowPosition, result\) → Ray

通过windowPosition 世界坐标中的像素从摄像机位置创建光线。

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| `windowPosition` | [Cartesian2](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html) | 像素的x和y坐标。 |
| `result` | [射线](https://cesiumjs.org/Cesium/Build/Documentation/Ray.html) | optional要存储结果的对象 |

返回Cartesian3光线的位置和方向。

# Ray

new Cesium.Ray\(origin, direction\)

表示在提供的方向上从提供的原点无限延伸的光线。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `origin` | [Cartesian3](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html) | `Cartesian3.ZERO` | 可选光线的原点。 |
| `direction` | [Cartesian3](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html) | `Cartesian3.ZERO` | 可选射线的方向。 |



