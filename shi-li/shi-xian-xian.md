## 实现线

* 点的操作

执行：参数： viewer,lineoption,callback

```
function drawLine() {
    var lineOption = {
        width: 5,
        geodesic: true
    };
    DynamicDrawTool.startDrawingPolyshape(viewer, false, lineOption, function (cartesians) {
        //下面对处理代码
        //....
    });
}
```

动态绘制工具

```
var DynamicDrawTool = (function(){
    var mouseHandlerDraw; //鼠标控制句柄
    var ellipseoid = Cesium.Ellipsoid.WGS84; //浏览器WGS84地图球体

    function _(){};

    //ChangeablePrimtive -子目录ChangeablePrimtive 可变的实体基类

    //PolylinePrimtitve -子目录PolylinePrimtitve 折线

    //PolygonPrimitive 多边形

    //画点
    _.startDrawingMarker = function (viewer, msg, callback) {
        var scene = viewer.scene;
        if (mouseHandlerDraw) {
            mouseHandlerDraw.destroy();
            mouseHandlerDraw = null;
        } else {
            mouseHandlerDraw = new Cesium.ScreenSpaceEventHandler(scene.canvas);
        }
        CesiumTooltip.initTool(viewer);
        //点击获取点击的位置
        mouseHandlerDraw.setInputAction(function (movement) {
            if (movement.position != null) {
            //
                var cartesian = scene.camera.pickEllipsoid(movement.position, ellipsoid);
                if (cartesian) {
                    //if (callback) {
                    if (typeof callback == 'function') {
                        callback(cartesian);
                    }
                }
                if (mouseHandlerDraw) {
                    mouseHandlerDraw.destroy();
                    mouseHandlerDraw = null;

                }
                if (CesiumTooltip) {
                    CesiumTooltip.setVisible(false);
                }
            }
        }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
        //移动，tiptool跟随
        mouseHandlerDraw.setInputAction(function (movement) {
            var position = movement.endPosition;
            if (position != null) {
                var cartesian = scene.camera.pickEllipsoid(position, ellipsoid);
                if (cartesian) {
                    CesiumTooltip.showAt(position, msg + "\n位置:" + getDisplayLatLngString(ellipsoid.cartesianToCartographic(cartesian)));
                } else {
                    CesiumTooltip.showAt(position, msg);
                }
            }
        }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);
    }
    
    //开始绘制多边形
    _.startDrawingPolyshape = function (viewer, isPolygon, PolyOption, callback) {
        var scene = viewer.scene;
        if (mouseHandlerDraw) {
            mouseHandlerDraw.destroy();
            mouseHandlerDraw = null;
        } else {
            mouseHandlerDraw = new Cesium.ScreenSpaceEventHandler(scene.canvas);
        }

        CesiumTooltip.initTool(viewer);
        
        var minPoints = isPolygon ? 3 : 2;
        var primitives = scene.primitives;
        var poly;
        //声明线或者多边形实体
        if (isPolygon) {
            poly = new PolygonPrimitive(PolyOption);
        } else {
            poly = new PolylinePrimitive(PolyOption);
        }
        
                
    });
});
```

* 线的实现



