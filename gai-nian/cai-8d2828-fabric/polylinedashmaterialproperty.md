# PolylineDashMaterialProperty

映射到折线破折号材质

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `color` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.WHITE` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)行的属性。 |
| `gapColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.TRANSPARENT` | optional一个属性，指定行[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)中的间隙。 |
| `dashLength` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `16.0` | optional一个数字属性，指定pixel.s中的虚线模式的长度 |
| `dashPattern` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `255.0` | optional一个数字属性，指定短划线的16位模式 |

#### 实例

```
//entities -> add -> polyline
material : new Cesium.PolylineDashMaterialProperty({
 color: Cesium.Color.CYAN
})
```



