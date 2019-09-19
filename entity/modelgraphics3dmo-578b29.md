# ModelGraphics

* 基于glTF的 3D模型，glTF是WebGL，Op​​enGL ES和OpenGL的运行时资产格式。模型的位置和方向由包含确定Entity。
* Cesium包括对glTF几何，材质，动画和蒙皮的支持。目前不支持相机和灯光。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定模型的可见性。 |
| `uri` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个字符串或Resource属性，指定glTF资产的URI。 |
| `scale` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `1.0` | optional一个指定均匀线性比例的数字属性。 |
| `minimumPixelSize` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | 可选数字属性，指定模型的近似最小像素大小，与缩放无关。 |
| `maximumScale` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | 可选模型的最大比例尺寸。minimumPixelSize的上限。 |
| `incrementallyLoadTextures` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional确定在加载模型后纹理是否可以继续流入。 |
| `runAnimations` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个boolean属性，指定是否应该启动模型中指定的glTF动画。 |
| `clampAnimations` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `true` | optional一个布尔属性，指定glTF动画是否应保留最后一个没有关键帧的持续时间姿势。 |
| `shadows` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ShadowMode.ENABLED` | optional枚举属性，指定模型是否从每个光源投射或接收阴影。 |
| `heightReference` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `HeightReference.NONE` | optional一个属性，指定高度相对于什么。 |
| `silhouetteColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.RED` | optional一个指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)轮廓的属性。 |
| `silhouetteSize` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.0` | optional一个数字属性，指定轮廓的大小（以像素为单位）。 |
| `color` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `Color.WHITE` | optional一个属性，指定[`Color`](https://cesiumjs.org/Cesium/Build/Documentation/Color.html)与模型的渲染颜色混合的属性。 |
| `colorBlendMode` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `ColorBlendMode.HIGHLIGHT` | optional枚举属性，指定颜色与模型的混合方式。 |
| `colorBlendAmount` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `0.5` | 可选的数值属性指定的颜色强度时`colorBlendMode`是`MIX`。值0.0表示模型的渲染颜色，而值1.0表示纯色，中间任何值导致两者混合。 |
| `imageBasedLightingFactor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | `newCartesian2(1.0,1.0)` | optional一个属性，指定漫反射和镜面反射图像照明的贡献。 |
| `lightColor` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定着色模型时要使用的灯光颜色。当使用默认的太阳光颜色时`undefined`。 |
| `distanceDisplayCondition` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定与相机相距该模型的距离。 |
| `nodeTransformations` | [属性包](https://cesiumjs.org/Cesium/Build/Documentation/PropertyBag.html) |  | 可选对象，其中键是节点的名称，值是[`TranslationRotationScale`](https://cesiumjs.org/Cesium/Build/Documentation/TranslationRotationScale.html)描述要应用于该节点的转换的属性。转换在glTF中指定的节点现有转换之后应用，并不替换节点的现有转换。 |
| `articulations` | [属性包](https://cesiumjs.org/Cesium/Build/Documentation/PropertyBag.html) |  | optional一个对象，其中键由清晰度名称，单个空格和阶段名称组成，值为数字属性。 |
| `clippingPlanes` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) |  | optional一个属性，指定[`ClippingPlaneCollection`](https://cesiumjs.org/Cesium/Build/Documentation/ClippingPlaneCollection.html)用于有选择地禁用渲染模型的属性。 |

#### 实例

```
viewer.entities.removeAll();

var position = Cesium.Cartesian3.fromDegrees(-123.0744619, 44.0503706, height);
var heading = Cesium.Math.toRadians(135);
var pitch = 0;
var roll = 0;
var hpr = new Cesium.HeadingPitchRoll(heading, pitch, roll);
var orientation = Cesium.Transforms.headingPitchRollQuaternion(position, hpr);

var entity = viewer.entities.add({
    name : url,
    position : position,
    orientation : orientation,
    model : {
        uri : url,
        minimumPixelSize : 128,
        maximumScale : 20000
    }
});
viewer.trackedEntity = entity;
```



