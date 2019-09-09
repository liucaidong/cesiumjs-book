#### 编辑状态节点 图标

BillboardGroup

```
_.BillboardGroup = function (changeablePrimitiveTool, options) {
    this.changeablePrimitiveTool = changeablePrimitiveTool;
    this._scene = changeablePrimitiveTool._scene;

    this._options = copyOptions(options, defaultBillboard);
    // create one common billboard collection for all billboards
    var b = new Cesium.BillboardCollection();
    this._scene.primitives.add(b);
    this._billboards = b;

    // keep an ordered list of billboards
    this._orderedBillboards = [];

   //设置属性方法 prototype.xxx 
   _.BillboardGroup.prototype.createBillboard = function (position, callbacks) {
   }
}
```

##### createBillboard 

创建节点

```
_.BillboardGroup.prototype.createBillboard = function (position, callbacks) {
     //添加广告牌
     var billboard = this._billboards.add({
          show: true,
          position: position,
          pixelOffset: new Cesium.Cartesian2(this._options.shiftX, this._options.shiftY),
          eyeOffset: new Cesium.Cartesian3(0.0, 0.0, 0.0),
          horizontalOrigin: Cesium.HorizontalOrigin.CENTER,
          verticalOrigin: Cesium.VerticalOrigin.CENTER,
          scale: 2.0,
          image: this._options.iconUrl,
          color: new Cesium.Color(1.0, 1.0, 1.0, 1.0)
     });   
     
     // if editable
     if (callbacks) {
		var _self = this;
		var screenSpaceCameraController = this._scene.screenSpaceCameraController;
		function enableRotation(enable) {
			screenSpaceCameraController.enableRotate = enable;
		}
		function getIndex() {
			// find index
			for (var i = 0, I = _self._orderedBillboards.length; i < I && _self._orderedBillboards[i] != billboard; ++i);
			return i;
		}
		if (callbacks.dragHandlers) {
			var _self = this;
			setListener(billboard, 'leftDown', function (position) {
				// TODO - start the drag handlers here
				// create handlers for mouseOut and leftUp for the billboard and a mouseMove
				function onDrag(position) {
					billboard.position = position;
					// find index
					for (var i = 0, I = _self._orderedBillboards.length; i < I && _self._orderedBillboards[i] != billboard; ++i);
					callbacks.dragHandlers.onDrag && callbacks.dragHandlers.onDrag(getIndex(), position);
				}
				function onDragEnd(position) {
					handler.destroy();
					enableRotation(true);
					callbacks.dragHandlers.onDragEnd && callbacks.dragHandlers.onDragEnd(getIndex(), position);
				}
		
				var handler = new Cesium.ScreenSpaceEventHandler(_self._scene.canvas);
		
				handler.setInputAction(function (movement) {
					var cartesian = _self._scene.camera.pickEllipsoid(movement.endPosition, ellipsoid);
					if (cartesian) {
						onDrag(cartesian);
					} else {
						onDragEnd(cartesian);
					}
				}, Cesium.ScreenSpaceEventType.MOUSE_MOVE);
		
				handler.setInputAction(function (movement) {
					onDragEnd(_self._scene.camera.pickEllipsoid(movement.position, ellipsoid));
				}, Cesium.ScreenSpaceEventType.LEFT_UP);
		
				enableRotation(false);
		
				callbacks.dragHandlers.onDragStart && callbacks.dragHandlers.onDragStart(getIndex(), _self._scene.camera.pickEllipsoid(position, ellipsoid));
			});
		}
		if (callbacks.onDoubleClick) {
			setListener(billboard, 'leftDoubleClick', function (position) {
				callbacks.onDoubleClick(getIndex());
			});
		}
		if (callbacks.onClick) {
			setListener(billboard, 'leftClick', function (position) {
				callbacks.onClick(getIndex());
			});
		}
		//处理提示窗事件
		if (callbacks.tooltip) {
			setListener(billboard, 'mouseMove', function (position) {
				//_self.changeablePrimitiveTool._tooltip.showAt(position, callbacks.tooltip());
				TooltipDiv.showAt(position, callbacks.tooltip());
			});
			setListener(billboard, 'mouseOut', function (position) {
				//_self.changeablePrimitiveTool._tooltip.setVisible(false);
				TooltipDiv.setVisible(false);
			});
		}
	}

	return billboard;
}
```

##### insertBillboard

```
_.BillboardGroup.prototype.insertBillboard = function (index, position, callbacks) {
    this._orderedBillboards.splice(index, 0, this.createBillboard(position, callbacks));
```

##### addBillboard

```
_.BillboardGroup.prototype.addBillboard = function (position, callbacks) {
 this._orderedBillboards.push(this.createBillboard(position, callbacks));
};
```

##### addBillboards

```
_.BillboardGroup.prototype.addBillboards = function (positions, callbacks) {
    var index = 0;
    for (; index < positions.length; index++) {
        this.addBillboard(positions[index], callbacks);
    }
};
```

##### updateBillboardsPositions

```
_.BillboardGroup.prototype.updateBillboardsPositions = function (positions) {
    var index = 0;
    for (; index < positions.length; index++) {
        this.getBillboard(index).position = positions[index];
    }
};
```

##### getBillboard

```
_.BillboardGroup.prototype.getBillboard = function (index) {
    return this._orderedBillboards[index];
};
```

##### removeBillboard

```
_.BillboardGroup.prototype.removeBillboard = function (index) {
    this._billboards.remove(this.getBillboard(index));
    this._orderedBillboards.splice(index, 1);
};
```

##### remove

```
_.BillboardGroup.prototype.remove = function () {
    this._billboards = this._billboards && this._billboards.removeAll() && this._billboards.destroy();
};
```

##### setOnTop

```
_.BillboardGroup.prototype.setOnTop = function () {
    this._scene.primitives.raiseToTop(this._billboards);
};
```



