## ChangeablePrimitiveTool

画线

##### PolylinePrimitive : setEditable

```
//添加属性方法：setEditable
ChangeablePrimitiveTool.PolylinePrimitive.prototype.setEditable = function () {
    if (this.setEditMode) {
        return;
    }

    var polyline = this;
    polyline.isPolygon = false;
    polyline.asynchronous = false;

    changeablePrimitiveTool.registerEditableShape(polyline);

    polyline.setEditMode = setEditMode;

    var originalWidth = this.width;

    polyline.setHighlighted = function (highlighted) {
        // disable if already in edit mode
        if (this._editMode === true) {
            return;
        }
        if (highlighted) {
            changeablePrimitiveTool.setHighlighted(this);
            this.setWidth(originalWidth * 2);
        } else {
            this.setWidth(originalWidth);
        }
    };

    polyline.getExtent = function () {
        return Cesium.Extent.fromCartographicArray(ellipsoid.cartesianArrayToCartographicArray(this.positions));
    };

    //添加监听
    enhanceWithListeners(polyline);
    polyline.setEditMode(false);
};
```

##### PolylinePrimitive：setEditableFalse



