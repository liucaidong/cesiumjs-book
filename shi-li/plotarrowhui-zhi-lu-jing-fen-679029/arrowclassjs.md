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
    startModify: function(){},//修改箭头
    createByData: function(data){} //通过传入经纬度数组 构建箭头
}
```

##### startModify

* chickStep

```
startModify: function() { //修改箭头
    this.state = 2;
    this.firstPoint.show = true;
    this.floatPoint.show = true;
    var $this = this;
    this.clickStep = 0;
    if (!this.modifyHandler) this.modifyHandler = new Cesium.ScreenSpaceEventHandler(this.viewer.scene.canvas);
    this.modifyHandler.setInputAction(function(evt) { //单机开始绘制
        var pick = $this.viewer.scene.pick(evt.position);
        if (Cesium.defined(pick) && pick.id) {
            $this.clickStep++;
            if(!pick.id.objId) 
                $this.selectPoint = pick.id;
        } else { //激活移动点之后 单机面之外 移除这个事件
            $this.modifyHandler.destroy(); 
            $this.modifyHandler = null;
            $this.firstPoint.show = false;
            $this.floatPoint.show = false;
            $this.state = -1;
        }
        if ($this.clickStep == 2) { //选中点后 第二次点击 则重新定位该点
            $this.clickStep = 0;
            $this.clickStep == 0;
            var ray = $this.viewer.camera.getPickRay(evt.position);
            if (!ray) return;
            var cartesian = $this.viewer.scene.globe.pick(ray, $this.viewer.scene);
            if($this.selectPoint){
                $this.selectPoint.position.setValue(cartesian);
                $this.selectPoint = null;
            }

        };
    }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
    this.modifyHandler.setInputAction(function(evt) { //单机开始绘制
        var ray = $this.viewer.camera.getPickRay(evt.endPosition);
        if (!ray) return;
        var cartesian = $this.viewer.scene.globe.pick(ray, $this.viewer.scene);
        if ($this.selectPoint) {
            $this.selectPoint.position.setValue(cartesian);
            if ($this.selectPoint.type == "firstPoint") {
                $this.positions[1] = cartesian;
            } else {
                $this.positions[2] = cartesian;
            }
        } else {
            return;
        }
    }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);
},
```

##### startDraw

* creatPoint ???
* positions.length
  * ==0 创建firstPoint floatPoint
  * ==3 state = -1 
  * arrowEntity ??
* showArrowOnMap\(\) ???

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



