## 可编辑绘制

##### 使用：

```
//化线
function drawLine() {
    viewer.scene.primitives.removeAll();
    var positionWord = [];
    positionWord.push(Cesium.Cartesian3.fromDegrees(110.20, 34.55, 0));
    positionWord.push(Cesium.Cartesian3.fromDegrees(115.20, 34.55, 0));
    positionWord.push(Cesium.Cartesian3.fromDegrees(115.20, 39.55, 0));
    //生成线
    var polyline = new ChangeablePrimitiveTool.PolylinePrimitive({
        positions: positionWord,
        width: 5,
        geodesic: true,
        objId: new Date().getTime() + 'id',
        //material: materialLine
    }, viewer);
    viewer.scene.primitives.add(polyline);
    polyline.setEditable();
    //添加监听事件
    polyline.addListener('onEdited', function (event) {
        var msg = '';
        if (event.objId) {
            msg = '编辑多段线,共' + event.positions.length + '个点-' + event.objId;
        } else {
            msg = '编辑多段线,共' + event.positions.length + '个点';
        }
        alert( msg);
    });
}
```

##### 可编辑工具

```
var ChangeablePrimitiveTool = (function () {
    //变量
    var isCreat = false;
    var ellipsoid = Cesium.Ellipsoid.WGS84;
    var materialLine = Cesium.Material.fromType(Cesium.Material.ColorType);
    materialLine.uniforms.color = new Cesium.Color(1.0, 1.0, 0.0, 0.5);

    var materialSurface = Cesium.Material.fromType(Cesium.Material.ColorType);
    materialSurface.uniforms.color = new Cesium.Color(0.0, 1.0, 1.0, 0.5);

    //属性
    var defaultShapeOptions = {
        ellipsoid: Cesium.Ellipsoid.WGS84,
        textureRotationAngle: 0.0,
        height: 0.0,
        asynchronous: true,
        show: true,
        debugShowBoundingVolume: false
    };
    var defaultSurfaceOptions = copyOptions(defaultShapeOptions, {
        appearance: new Cesium.EllipsoidSurfaceAppearance({
            aboveGround: false
        }),
        material: materialSurface,
        granularity: Math.PI / 180.0
    });

    var defaultPolylineOptions = copyOptions(defaultShapeOptions, {
        width: 5,
        geodesic: true,
        granularity: 10000,
        appearance: new Cesium.PolylineMaterialAppearance({
            aboveGround: false
        }),
        material: materialLine
    });
    var defaultPolygonOptions = copyOptions(defaultSurfaceOptions, {}); 
    //编辑状态节点图标
    var defaultBillboard = {
        iconUrl: "./sampledata/images/dragIcon.png",
        shiftX: 0,
        shiftY: 0
    };
    var dragBillboard = {
        iconUrl: "./sampledata/images/dragIcon.png",
        shiftX: 0,
        shiftY: 0
    };
    var dragHalfBillboard = {
        iconUrl: "./sampledata/images/dragIconLight.png",
        shiftX: 0,
        shiftY: 0
    };

    var ChangeablePrimitive = ()//子目录下 可变实体

    /**
     * _构造函数
     * @param cesiumWidget
     * @private
     */
    function _(viewer) {
        this._scene = viewer.scene;
        //this._tooltip = createTooltip(viewer.cesiumWidget.container);
        TooltipDiv.initTool(viewer.cesiumWidget.container);
        this._surfaces = [];

        this.initialiseHandlers();
        this.enhancePrimitives();
        isCreat = true;
    }

    //注册编辑事件
    // shape should implement setEditMode and setHighlighted
    _.prototype.registerEditableShape = function (surface) {
        var _self = this;
        // handlers for interactions
        // highlight polygon when mouse is entering
        setListener(surface, 'mouseMove', function (position) {
            surface.setHighlighted(true);
            if (!surface._editMode) {
                //_self._tooltip.showAt(position, "点击编辑结点");
                TooltipDiv.showAt(position, "点击编辑结点");
            }
        });
        // hide the highlighting when mouse is leaving the polygon
        setListener(surface, 'mouseOut', function (position) {
            surface.setHighlighted(false);
            //_self._tooltip.setVisible(false);
            TooltipDiv.setVisible(false);
        });
        setListener(surface, 'leftClick', function (position) {
            surface.setEditMode(true);
        });
    };

     _.prototype.initialiseHandlers = function () {
        var scene = this._scene;
        var _self = this;
        // scene events
        var handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
        //执行方法
        function callPrimitiveCallback(name, position) {
            if (_self._handlersMuted == true) return;
            var pickedObject = scene.pick(position);
            if (pickedObject && pickedObject.primitive && pickedObject.primitive[name]) {
                pickedObject.primitive[name](position);
            }
        }
        handler.setInputAction(
            function (movement) {
                callPrimitiveCallback('leftClick', movement.position);
            }, Cesium.ScreenSpaceEventType.LEFT_CLICK);
        handler.setInputAction(
            function (movement) {
                callPrimitiveCallback('leftDoubleClick', movement.position);
            }, Cesium.ScreenSpaceEventType.LEFT_DOUBLE_CLICK);
        var mouseOutObject;
        handler.setInputAction(
            function (movement) {
                if (_self._handlersMuted == true) return;
                var pickedObject = scene.pick(movement.endPosition);
                if (mouseOutObject && (!pickedObject || mouseOutObject != pickedObject.primitive)) {
                    !(mouseOutObject.isDestroyed && mouseOutObject.isDestroyed()) && mouseOutObject.mouseOut(movement.endPosition);
                    mouseOutObject = null;
                }
                if (pickedObject && pickedObject.primitive) {
                    pickedObject = pickedObject.primitive;
                    if (pickedObject.mouseOut) {
                        mouseOutObject = pickedObject;
                    }
                    if (pickedObject.mouseMove) {
                        pickedObject.mouseMove(movement.endPosition);
                    }
                }
            }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);
        handler.setInputAction(
            function (movement) {
                callPrimitiveCallback('leftUp', movement.position);
            }, Cesium.ScreenSpaceEventType.LEFT_UP);
        handler.setInputAction(
            function (movement) {
                callPrimitiveCallback('leftDown', movement.position);
            }, Cesium.ScreenSpaceEventType.LEFT_DOWN);
    };
    
    return _;
}());
```



