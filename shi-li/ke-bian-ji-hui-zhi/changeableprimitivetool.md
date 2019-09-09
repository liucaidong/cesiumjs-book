## ChangeablePrimitiveTool

#### PolylinePrimitive 

画线

##### PolylinePrimitive : setEditable

设置可编辑

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

设置不可编辑

```
//取消编辑状态 -- 在外层控制 
ChangeablePrimitiveTool.PolylinePrimitive.prototype.setEditableFalse = function () {
    var polyline = this;
    if (polyline.setEditMode) {
        polyline.setEditMode(false);
    }
}
```

#### PolygonPrimitive

画多边型

##### setEditable：设置可编辑

```
ChangeablePrimitiveTool.PolygonPrimitive.prototype.setEditable = function () {

	var polygon = this;
	polygon.asynchronous = false;

	var scene = changeablePrimitiveTool._scene;

	changeablePrimitiveTool.registerEditableShape(polygon);

	polygon.setEditMode = setEditMode;

	polygon.setHighlighted = setHighlighted;

	enhanceWithListeners(polygon);

	polygon.setEditMode(false);
};
```

##### setEditableFalse：设置不可编辑

```
//取消编辑状态 -- 在外层控制 
ChangeablePrimitiveTool.PolygonPrimitive.prototype.setEditableFalse = function () {
    var polygon = this;
    if (polygon.setEditMode) {
        polygon.setEditMode(false);
    }
}
```



