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

简明使用

1. 声明Cesium.createWorldTerrain，newCesium.CesiumTerrainProvider
2. 使用viewer.terrainProvider = 

**例子**

```
//在线地形
var worldTerrain = Cesium.createWorldTerrain({
    requestWaterMask: true,
    requestVertexNormals: true
});
//使用
viewer.terrainProvider = ellipsoidProvider;//地形数据源
```

#### \#图层

打开图层选择器

```
{
     baseLayerPicker: false, //是否显示图层选择控件
}
```

选择默认图层

```
viewer.baseLayerPicker.viewModel.selectedImagery = viewer.baseLayerPicker.viewModel.imageryProviderViewModels[6];
```

自定义图层

```
//1new Cesium.ProviderViewModel声明图层模型
var providerViewModels = [];
var esriMapModel = new Cesium.ProviderViewModel({
    name: 'esri Maps',
    iconUrl: Cesium.buildModuleUrl('./Widgets/Images/ImageryProviders/esriWorldImagery.png'),
    tooltip: 'ArcGIS 地图服务 \nhttps://services.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer',
    creationFunction: function () {
        return esriMap;
    }
});
providerViewModels.push(esriMapModel);
//2 使用自定义图层选择器
{imageryProviderViewModels: providerViewModels, }
```



