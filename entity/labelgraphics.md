# LabelGraphics

```
new Cesium.LabelGraphics(options)
```

描述位于包含位置的二维标签

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定标签的可见性。 |
| `text` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个指定文本的属性。支持显式换行符' n'。 |
| `font` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `'30px sans-serif'` | optional一个指定CSS字体的属性。 |
| `style` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `LabelStyle.FILL` | optional一个指定的属性[`LabelStyle`](https://cesiumjs.org/Cesium/Build/Documentation/LabelStyle.html)。 |
| `scale` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个数字属性，指定要应用于文本的比例。 |
| `showBackground` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `false` | optional一个布尔属性，指定标签后面背景的可见性。 |
| `backgroundColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `newColor(0.165,0.165,0.165,0.8)` | optional一个指定背景的属性[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)。 |
| `backgroundPadding` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `newCartesian2(7,5)` | optional一个[`Cartesian2`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html)属性，指定水平和垂直背景填充（以像素为单位）。 |
| `pixelOffset` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cartesian2.ZERO` | optional一个[`Cartesian2`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html)指定像素偏移的属性。 |
| `eyeOffset` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cartesian3.ZERO` | optional一个[`Cartesian3`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)指定眼睛偏移的属性。 |
| `horizontalOrigin` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `HorizontalOrigin.CENTER` | optional一个指定的属性[`HorizontalOrigin`](https://cesiumjs.org/Cesium/Build/Documentation/HorizontalOrigin.html)。 |
| `verticalOrigin` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `VerticalOrigin.CENTER` | optional一个指定的属性[`VerticalOrigin`](https://cesiumjs.org/Cesium/Build/Documentation/VerticalOrigin.html)。 |
| `heightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `HeightReference.NONE` | optional一个属性，指定高度相对于什么。 |
| `fillColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.WHITE` | optional一个指定填充的属性[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)。 |
| `outlineColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.BLACK` | optional一个指定轮廓的属性[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)。 |
| `outlineWidth` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个指定轮廓宽度的数字属性。 |
| `translucencyByDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选甲[`NearFarScalar`](https://cesiumjs.org/Cesium/Build/Documentation/NearFarScalar.html)属性时使用的基于从摄像机的距离来设置透光性。 |
| `pixelOffsetScaleByDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个[`NearFarScalar`](https://cesiumjs.org/Cesium/Build/Documentation/NearFarScalar.html)属性，用于根据与摄像机的距离设置pixelOffset。 |
| `scaleByDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选的一个[`NearFarScalar`](https://cesiumjs.org/Cesium/Build/Documentation/NearFarScalar.html)属性用于基于从相机的距离来设定规模。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定与相机相隔的距离，此标签将显示。 |
| `disableDepthTestDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定从相机到禁用深度测试的距离。 |

##### 例子

```
viewer.entities.add({
        position : Cesium.Cartesian3.fromDegrees(-75.1641667, 39.9522222),
        label : {
            text : 'Philadelphia'
        }
    });

```



