#### initialiseHandlers

初始化

```
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
```

* leftClick - LEFT\_CLICK
* leftDoubleClick - LEFT\_DOUBLE\_CLICK
*  - MOUSE\_MOVE
* leftUp - LEFT\_UP
* leftDown - LEFT\_DOWN



