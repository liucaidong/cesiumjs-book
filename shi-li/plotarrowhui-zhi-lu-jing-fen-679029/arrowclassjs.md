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
    disable: function(){},
    startDraw： function(){},
}
```

##### startDraw

```
startDraw: function() {
    var $this = this;
    this.state = 1; //状态
    this.handler.setInputAction(function(evt) { //单机开始绘制
        var ray = viewer.camera.getPickRay(evt.position);
        if (!ray) return;
        var cartesian = viewer.scene.globe.pick(ray, $this.viewer.scene);
        if ($this.positions.length == 0) {
            $this.firstPoint = $this.creatPoint(cartesian);
            $this.firstPoint.type = "firstPoint";
            $this.floatPoint = $this.creatPoint(cartesian);
            $this.floatPoint.type = "floatPoint";
            $this.positions.push(cartesian);
        }
        if ($this.positions.length == 3) {
            $this.firstPoint.show = false;
            $this.floatPoint.show = false;
            $this.handler.destroy();
            $this.arrowEntity.objId = $this.objId;
            $this.state = -1;
        }
        $this.positions.push(cartesian.clone());
    }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
    this.handler.setInputAction(function(evt) { //移动时绘制面
        if ($this.positions.length < 1) return;
        var ray = viewer.camera.getPickRay(evt.endPosition);
        if (!ray) return;
        var cartesian = viewer.scene.globe.pick(ray, $this.viewer.scene);
        $this.floatPoint.position.setValue(cartesian);
        if ($this.positions.length >= 2) {
            if (!Cesium.defined($this.arrowEntity)) {
                $this.positions.push(cartesian);
                $this.arrowEntity = $this.showArrowOnMap($this.positions);

            } else {
                $this.positions.pop();
                $this.positions.push(cartesian);
            }
        }
    }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);
},
```

##### disable -销毁当前绘制功能

* firstPoint floatPoint arrowEntity handler selectPoint modifyHandler 等

```
disable: function() {
    this.positions = [];
    if (this.firstPoint) {
        this.viewer.entities.remove(this.firstPoint);
        this.firstPoint = null;
    }
    if (this.floatPoint) {
        this.viewer.entities.remove(this.floatPoint);
        this.floatPoint = null;
    }
    if (this.arrowEntity) {
        this.viewer.entities.remove(this.arrowEntity);
        this.arrowEntity = null;
    }
    this.state = -1;
    if (this.handler) {
        this.handler.destroy();
        this.handler = new Cesium.ScreenSpaceEventHandler(this.viewer.scene.canvas);
    }
    if (this.selectPoint) {
        this.viewer.entities.remove(this.selectPoint);
        this.selectPoint = null;
    }
    if (this.modifyHandler) {
        this.modifyHandler.destroy();
        this.modifyHandler = null;
    }
    this.clickStep = 0;
},
```



