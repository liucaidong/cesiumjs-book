# -影像服务&地形服务

#### \#影像服务

最基础的例子，提供地图简单的影像服务

**例子**

```
// 影像服务
var esri = new Cesium.ArcGisMapServerImageryProvider({
    url: 'https://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer',
    enablePickFeatures: false
});
//初始化地图
var viewer = new Cesium.Viewer('cesiumContainer',{
    imageryProvider: esri,
    contextOptions: {
        webgl: {
            alpha: true
        }
    },
    creditContainer: "creditContainer",
    selectionIndicator: false,
    animation: false,  //是否显示动画控件
    baseLayerPicker: false, //是否显示图层选择控件
    geocoder: false, //是否显示地名查找控件
    timeline: false, //是否显示时间线控件
    sceneModePicker: true, //是否显示投影方式控件
    navigationHelpButton: false, //是否显示帮助信息控件
    infoBox: false,  //是否显示点击要素之后显示的信息
    fullscreenButton: true
});
```

该文章只是简明的基础篇，影像服务有 1自带在线影像服务 2在线扩展的影像服务 3自己处理瓦片数据的影像服务 就不一一列举出来

#### \#地形服务



```
//在线地形
var worldTerrain = Cesium.createWorldTerrain({
    requestWaterMask: true,
    requestVertexNormals: true
});
//使用
viewer.terrainProvider = ellipsoidProvider;//地形数据源
```



