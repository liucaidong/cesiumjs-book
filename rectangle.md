# Rectangle

指定为经度和纬度坐标的二维区域。

```
new Cesium.Rectangle(west, south, east, north)
```

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `west` | 数 | `0.0` | 可选的最西经度，以弧度表示，范围为\[-Pi，Pi\]。 |
| `south` | 数 | `0.0` | 可选最南端的纬度，以弧度为单位，范围为\[-Pi / 2，Pi / 2\]。 |
| `east` | 数 | `0.0` | 可选的最东经度，以弧度表示，范围为\[-Pi，Pi\]。 |
| `north` | 数 | `0.0` | 可选最北纬度，以弧度表示，范围为\[-Pi / 2，Pi / 2\]。 |

### Methods

```
Cesium.Rectangle.fromDegrees(west, south, east, north, result) → Rectangle
```

给定边界经度和纬度（以度为单位）的矩形。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `west` | 数 | `0.0` | 可选的最西经度，范围为\[-180.0,180.0\]。 |
| `south` | 数 | `0.0` | 可选范围最南端的纬度，范围为\[-90.0,90.0\]。 |
| `east` | 数 | `0.0` | 可选的最东经度，范围为\[-180.0,180.0\]。 |
| `north` | 数 | `0.0` | 可选最近的纬度，范围为\[-90.0,90.0\]。 |
| `result` | [长方形](https://cesiumjs.org/Cesium/Build/Documentation/Rectangle.html) |  | optional要存储结果的对象，如果应创建新实例，则为undefined。 |

##### 返回：

修改后的结果参数或新的Rectangle实例（如果未提供）。

##### 例子

```
var rectangle = Cesium.Rectangle.fromDegrees(0.0, 20.0, 10.0, 30.0);
```



