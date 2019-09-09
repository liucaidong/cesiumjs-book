#### enhancePrimitives

```
_.prototype.enhancePrimitives = function () {
    var changeablePrimitiveTool = this;

    Cesium.Billboard.prototype.setEditable = function () {
        if (this._editable) {
            return;
        }

        this._editable = true;
        var billboard = this;
        var _self = this;
        function enableRotation(enable) {
            changeablePrimitiveTool._scene.screenSpaceCameraController.enableRotate = enable;
        }
        //添加监听
        setListener(billboard, 'leftDown', function (position) {
            // TODO - start the drag handlers here
            // create handlers for mouseOut and leftUp for the billboard and a mouseMove
            function onDrag(position) {
                billboard.position = position;
                _self.executeListeners({ name: 'drag', positions: position });
            }
            function onDragEnd(position) {
                handler.destroy();
                enableRotation(true);
                _self.executeListeners({ name: 'dragEnd', positions: position });
            }

            var handler = new Cesium.ScreenSpaceEventHandler(changeablePrimitiveTool._scene.canvas);

            handler.setInputAction(function (movement) {
                var cartesian = changeablePrimitiveTool._scene.camera.pickEllipsoid(movement.endPosition, ellipsoid);
                if (cartesian) {
                    onDrag(cartesian);
                } else {
                    onDragEnd(cartesian);
                }
            }, Cesium.ScreenSpaceEventType.MOUSE_MOVE);

            handler.setInputAction(function (movement) {
                onDragEnd(changeablePrimitiveTool._scene.camera.pickEllipsoid(movement.position, ellipsoid));
            }, Cesium.ScreenSpaceEventType.LEFT_UP);

            enableRotation(false);

        });
        
        enhanceWithListeners(billboard);
    };
    
    function setHighlighted(highlighted) {
        var scene = changeablePrimitiveTool._scene;
        // if no change
        // if already highlighted, the outline polygon will be available
        if (this._highlighted && this._highlighted == highlighted) {
            return;
        }
        
    }
}
```



