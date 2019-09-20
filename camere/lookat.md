#### lookAt\(target, offset\) {#lookAt}

使用目标和偏移设置摄像机位置和方向。目标必须以世界坐标给出。偏移可以是以目标为中心的局部东 - 北 - 向上参考系中的笛卡尔坐标或航向/俯仰/范围。如果偏移是笛卡尔坐标，那么它是距转换矩阵定义的参考系中心的偏移量。如果偏移是航向/俯仰/范围，则航向和俯仰角在由变换矩阵定义的参考系中定义。航向是从y轴开始朝向x轴增加的角度。间距是从xy平面的旋转。正俯仰角在平面下方。负俯仰角在平面上方。范围是距离中心的距离。在2D中，必须有一个自上而下的视图。相机将放在目标上方向下看。目标上方的高度将是偏移量的大小。标题将根据偏移确定。如果无法从偏移确定航向，则航向将为北。

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| `target` | [Cartesian3](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html) | 世界坐标中的目标位置。 |
| `offset` | [笛卡儿3](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian3.html)\|[HeadingPitchRange](https://cesiumjs.org/Cesium/Build/Documentation/HeadingPitchRange.html) | 距离目标的本地东 - 北 - 向上参考系中目标的偏移量 |

```
view2D.scene.camera.lookAt(worldPosition, new Cesium.Cartesian3(0.0, 0.0, distance));
```



