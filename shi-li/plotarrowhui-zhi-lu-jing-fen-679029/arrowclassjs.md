## arrowClass.js

#### StraightArrow -直线路径

```
var StraightArrow = function(viewer) {
    this.type = "StraightArrow";
    this.objId = Number((new Date()).getTime()+ "" +Number(Math.random()*1000).toFixed(0)); //用于区分多个相同箭头时

    this.viewer = viewer;
    this.handler = new Cesium.ScreenSpaceEventHandler(this.viewer.scene.canvas);
    this.pointImageUrl = "img/point.png";
    this.fillMaterial = Cesium.Color.fromCssColorString('#0000FF').withAlpha(0.5);
    this.outlineMaterial = new Cesium.PolylineDashMaterialProperty({
        dashLength: 16,
        color: Cesium.Color.fromCssColorString('#f00').withAlpha(0.7)
    });
    this.positions = [];
    this.firstPoint = null;
    this.floatPoint = null;
    this.arrowEntity = null;
    this.state = -1; //state用于区分当前的状态 0 为删除 1为添加 2为编辑 
    this.selectPoint = null;
    this.clickStep = 0;
    this.modifyHandler = null;
}
```

##### StraightArrow.prototype

```
StraightArrow.prototype = {
    this.positions = [],
    
}
```



