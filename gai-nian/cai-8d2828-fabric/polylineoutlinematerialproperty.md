# PolylineOutlineMaterialProperty

映射到折线轮廓材质

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `color` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.WHITE` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)行的属性。 |
| `outlineColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.BLACK` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)轮廓的属性。 |
| `outlineWidth` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | 可选指定轮廓宽度的数字属性，以像素为单位。 |

#### 实例

```
material : new Cesium.PolylineOutlineMaterialProperty({
    color : Cesium.Color.ORANGE,
    outlineWidth : 2,
    outlineColor : Cesium.Color.BLACK
})
```



