## Cesium.Scene

所有3D图形对象的容器，并在Cesium虚拟场景中显示

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `canvas` | 帆布 |  | 用于创建场景的HTML canvas元素。 |
| `contextOptions` | 宾语 |  | 可选的Context和WebGL创建属性。详见上文。 |
| `creditContainer` | 元件 |  | 可选将显示学分的HTML元素。 |
| `creditViewport` | 元件 |  | 可选用于显示信用弹出窗口的HTML元素。如果未指定，则视口将作为画布的兄弟添加。 |
| `mapProjection` | [MapProjection](https://cesiumjs.org/Cesium/Build/Documentation/MapProjection.html) | `newGeographicProjection()` | 可选用于2D和Columbus View模式的地图投影。 |
| `orderIndependentTranslucency` | 布尔 | `true` | optional如果为true且配置支持它，请使用与顺序无关的半透明。 |
| `scene3DOnly` | 布尔 | `false` | optional如果为true，则优化3D模式的内存使用和性能，但禁用使用2D或Columbus View的功能。 |
| `terrainExaggeration` | 数 | `1.0` | 可选用于夸大地形的标量。请注意，地形夸大不会修改任何其他基元，因为它们相对于椭球定位。 |
| `shadows` | 布尔 | `false` | 可选确定是否由太阳投射阴影。 |
| `mapMode2D` | [MapMode2D](https://cesiumjs.org/Cesium/Build/Documentation/MapMode2D.html) | `MapMode2D.INFINITE_SCROLL` | 可选确定2D地图是可旋转的还是可以在水平方向上无限滚动。 |
| `requestRenderMode` | 布尔 | `false` | optional如果为true，则渲染帧仅在需要时才会出现，具体取决于场景中的更改。启用可提高应用程序的性能，但需要使用[`Scene#requestRender`](https://cesiumjs.org/Cesium/Build/Documentation/Scene.html#requestRender)此模式显式呈现新帧。在API的其他部分中对场景进行更改后，在许多情况下这是必要的。请参阅[使用显式渲染提高性能](https://cesium.com/blog/2018/01/24/cesium-scene-rendering-performance/)。 |
| `maximumRenderTimeChange` | 数 | `0.0` | optional如果requestRenderMode为true，则此值定义在请求呈现之前允许的模拟时间的最大更改。请参阅[使用显式渲染提高性能](https://cesium.com/blog/2018/01/24/cesium-scene-rendering-performance/)。 |



