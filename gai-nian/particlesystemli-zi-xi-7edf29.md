# ParticleSystem

new Cesium.ParticleSystem\(options\)

粒子系统管理粒子集合的更新和显示。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `show` | 布尔 | `true` | 可选是否显示粒子系统。 |
| `updateCallback` | [粒子系统〜updateCallback](https://cesiumjs.org/Cesium/Build/Documentation/ParticleSystem.html#~updateCallback) |  | 可选在每帧中调用回调函数以更新粒子。 |
| `emitter` | [ParticleEmitter](https://cesiumjs.org/Cesium/Build/Documentation/ParticleEmitter.html) | `newCircleEmitter(0.5)` | 可选此系统的粒子发射器。 |
| `modelMatrix` | [Matrix4](https://cesiumjs.org/Cesium/Build/Documentation/Matrix4.html) | `Matrix4.IDENTITY` | 可选4x4转换矩阵，可将粒子系统从模型转换为世界坐标。 |
| `emitterModelMatrix` | [Matrix4](https://cesiumjs.org/Cesium/Build/Documentation/Matrix4.html) | `Matrix4.IDENTITY` | 可选4x4转换矩阵，用于转换粒子系统局部坐标系内的粒子系统发射器。 |
| `emissionRate` | 数 | `5` | 可选每秒发射的粒子数。 |
| `bursts` | Array。&lt;[ParticleBurst](https://cesiumjs.org/Cesium/Build/Documentation/ParticleBurst.html)&gt; |  | 可选的数组[`ParticleBurst`](https://cesiumjs.org/Cesium/Build/Documentation/ParticleBurst.html)，周期性地发射粒子爆发。 |
| `loop` | 布尔 | `true` | 可选粒子系统完成后是否应循环爆发。 |
| `scale` | 数 | `1.0` | 可选设置在其粒子寿命期间应用于粒子图像的比例。 |
| `startScale` | 数 |  | 可选在粒子寿命开始时应用于粒子图像的初始比例。 |
| `endScale` | 数 |  | 可选在粒子寿命结束时应用于粒子图像的最终比例。 |
| `color` | [颜色](https://cesiumjs.org/Cesium/Build/Documentation/Color.html) | `Color.WHITE` | 可选设置粒子在其粒子寿命期间的颜色。 |
| `startColor` | [颜色](https://cesiumjs.org/Cesium/Build/Documentation/Color.html) |  | 可选粒子寿命开始时的颜色。 |
| `endColor` | [颜色](https://cesiumjs.org/Cesium/Build/Documentation/Color.html) |  | 可选粒子寿命结束时的颜色。 |
| `image` | 宾语 |  | 可选用于广告牌的URI，HTMLImageElement或HTMLCanvasElement。 |
| `imageSize` | [Cartesian2](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html) | `newCartesian2(1.0,1.0)` | 可选如果设置，则覆盖用于以像素为单位缩放粒子图像尺寸的minimumImageSize和maximumImageSize输入。 |
| `minimumImageSize` | [Cartesian2](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html) |  | 可选设置宽度的最小界限，以高度为单位，在该界限之上可以随机缩放粒子图像的尺寸（以像素为单位）。 |
| `maximumImageSize` | [Cartesian2](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian2.html) |  | 可选设置最大宽度的高度范围，在该范围内可以随机缩放粒子图像的尺寸（以像素为单位）。 |
| `speed` | 数 | `1.0` | 可选如果设置，则使用此值覆盖minimumSpeed和maximumSpeed输入。 |
| `minimumSpeed` | 数 |  | optional设置以米/秒为单位的最小范围，在该范围上可以随机选择粒子的实际速度。 |
| `maximumSpeed` | 数 |  | 可选以秒为单位设置最大范围，在该范围内将随机选择粒子的实际速度。 |
| `lifetime` | 数 | `Number.MAX_VALUE` | 可选粒子系统发射粒子的时间，以秒为单位。 |
| `particleLife` | 数 | `5.0` | 可选如果设置，则使用此值覆盖minimumParticleLife和maximumParticleLife输入。 |
| `minimumParticleLife` | 数 |  | 可选以秒为单位设置粒子寿命可能的持续时间的最小范围，在该范围内将随机选择粒子的实际寿命。 |
| `maximumParticleLife` | 数 |  | 可选以秒为单位设置粒子生命的可能持续时间的最大范围，在该范围内可以随机选择粒子的实际生命。 |
| `mass` | 数 | `1.0` | 可选以千克为单位设置最小和最大颗粒质量。 |
| `minimumMass` | 数 |  | 可选设置粒子质量的最小范围（以千克为单位）。粒子的实际质量将被选择为高于此值的随机量。 |
| `maximumMass` | 数 |  | 可选以千克为单位设置最大粒子质量。粒子的实际质量将选择为低于此值的随机量。 |

```
var item = viewer.scene.primitives.add(new Cesium.ParticleSystem({
  image : getImage(),
  startColor : color,
  endColor : color.withAlpha(0.0),
  particleLife : 3.5,
  speed : 0.00005,
  imageSize : imageSize,
  emissionRate : 30.0,
  emitter : new Cesium.CircleEmitter(0.1),
  lifetime : 0.1,
  updateCallback : force,
  modelMatrix : particlesModelMatrix,
  emitterModelMatrix : emitterModelMatrix
}));
```



