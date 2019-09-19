# PolylineGlowMaterialProperty

映射到折线发光材质

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `color` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.WHITE` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)行的属性。 |
| `glowPower` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.25` | optional一个数字属性，指定发光强度，占总线宽的百分比。 |
| `taperPower` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个数字属性，指定逐渐减小效果的强度，以总线长度的百分比表示。如果为1.0或更高，则不使用锥度效果。 |

#### 实例

```
material : new Cesium.PolylineGlowMaterialProperty({
    glowPower : 0.2,
    taperPower : 0.5,
    color : Cesium.Color.CORNFLOWERBLUE
})
```



