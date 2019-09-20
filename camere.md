## camere

摄像机由位置，方向和视锥体定义。

方向形成具有视图的标准正交基础，向上和向右=视图x向上单位向量。

观察平截头体由6个平面定义。

每个平面由一个[`Cartesian4`](https://cesiumjs.org/Cesium/Build/Documentation/Cartesian4.html)对象表示，其中x，y和z分量定义垂直于平面的单位矢量，w分量是平面距原点/摄像机位置的距离。

* 翻译：相机

#### 事件

#### changed {#changed}

获取摄像机更改后将引发的事件percentageChanged。

```
view3D.camera.changed.addEventListener(sync2DView);
```



