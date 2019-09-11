# BillboardGraphics

```
new Cesium.BillboardGraphics(options)
```

描述位于包含位置的二维图标

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定广告牌的可见性。 |
| `image` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定要用于广告牌的图像，URI或画布。 |
| `scale` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个数字属性，指定要应用于图像大小的比例。 |
| `pixelOffset` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cartesian2.ZERO` | optional一个[`Cartesian2`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html)指定像素偏移的属性。 |
| `eyeOffset` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cartesian3.ZERO` | optional一个[`Cartesian3`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)指定眼睛偏移的属性。 |
| `horizontalOrigin` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `HorizontalOrigin.CENTER` | optional一个指定的属性[`HorizontalOrigin`](https://cesiumjs.org/Cesium/Build/Documentation/HorizontalOrigin.html)。 |
| `verticalOrigin` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `VerticalOrigin.CENTER` | optional一个指定的属性[`VerticalOrigin`](https://cesiumjs.org/Cesium/Build/Documentation/VerticalOrigin.html)。 |
| `heightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `HeightReference.NONE` | optional一个属性，指定高度相对于什么。 |
| `color` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.WHITE` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)图像色调的属性。 |
| `rotation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0` | optional一个数字属性，指定对齐alignedAxis的旋转。 |
| `alignedAxis` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Cartesian3.ZERO` | optional一个[`Cartesian3`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)属性，指定单位矢量旋转轴。 |
| `sizeInMeters` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个布尔属性，指定此广告牌的大小是否应以米为单位。 |
| `width` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个数字属性，指定广告牌的宽度（以像素为单位），覆盖原生大小。 |
| `height` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个数字属性，指定广告牌的高度（以像素为单位），覆盖原生大小。 |
| `scaleByDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选的一个[`NearFarScalar`](https://cesiumjs.org/Cesium/Build/Documentation/NearFarScalar.html)属性用于基于从相机的距离来缩放点。 |
| `translucencyByDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选甲[`NearFarScalar`](https://cesiumjs.org/Cesium/Build/Documentation/NearFarScalar.html)属性时使用的基于从摄像机的距离来设置透光性。 |
| `pixelOffsetScaleByDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个[`NearFarScalar`](https://cesiumjs.org/Cesium/Build/Documentation/NearFarScalar.html)属性，用于根据与摄像机的距离设置pixelOffset。 |
| `imageSubRegion` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选指定a的属性[`BoundingRectangle`](https://cesiumjs.org/Cesium/Build/Documentation/BoundingRectangle.html)，用于定义用于广告牌的图像的子区域，而不是整个图像，以左下角的像素为单位。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定与该摄像机的距离，以显示该广告牌。 |
| `disableDepthTestDistance` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定从相机到禁用深度测试的距离。 |

##### 例子

```
viewer.entities.add({
        position : Cesium.Cartesian3.fromDegrees(-75.59777, 40.03883),
        billboard :{
            image : '../images/Cesium_Logo_overlay.png'
        }
    });
```



