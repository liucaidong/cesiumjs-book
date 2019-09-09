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
        // disable if already in edit mode
        if (this._editMode === true) {
            return;
        }
        this._highlighted = highlighted;
        if (highlighted) {
            // make sure all other shapes are not highlighted
            changeablePrimitiveTool.setHighlighted(this);
            this._strokeColor = this.strokeColor;
            this.setStrokeStyle(Cesium.Color.fromCssColorString('white'), this.strokeWidth);
        } else {
            if (this._strokeColor) {
                this.setStrokeStyle(this._strokeColor, this.strokeWidth);
            } else {
                this.setStrokeStyle(undefined, undefined);
            }
        } 
    }
    
    function setEditMode(editMode) {
        if (this._editMode == editMode) {
            return;
        }
        // make sure all other shapes are not in edit mode before starting the editing of this shape
        changeablePrimitiveTool.disableAllHighlights();
        if (editMode) {
            changeablePrimitiveTool.setEdited(this);
            var scene = changeablePrimitiveTool._scene;
            var _self = this;
            // create the markers and handlers for the editing
            if (this._markers == null) {
                var markers = new _.BillboardGroup(changeablePrimitiveTool, dragBillboard);
                var editMarkers = new _.BillboardGroup(changeablePrimitiveTool, dragHalfBillboard);
                // function for updating the edit markers around a certain point
                function updateHalfMarkers(index, positions) {
                    // update the half markers before and after the index
                    var editIndex = index - 1 < 0 ? positions.length - 1 : index - 1;
                    if (editIndex < editMarkers.countBillboards()) {
                        editMarkers.getBillboard(editIndex).position = calculateHalfMarkerPosition(editIndex);
                    }
                    editIndex = index;
                    if (editIndex < editMarkers.countBillboards()) {
                        editMarkers.getBillboard(editIndex).position = calculateHalfMarkerPosition(editIndex);
                    }
                }
                function onEdited() {
                    //_self.executeListeners({ name: 'onEdited', positions: _self.positions });
                    _self.executeListeners({ name: 'onEdited', positions: _self.positions, objId: _self.objId });//添加对象id
                }
                var handleMarkerChanges = {
                    dragHandlers: {
                        onDrag: function (index, position) {
                            _self.positions[index] = position;
                            updateHalfMarkers(index, _self.positions);
                            _self._createPrimitive = true;
                        },
                        onDragEnd: function (index, position) {
                            _self._createPrimitive = true;
                            onEdited();
                        }
                    },
                    onDoubleClick: function (index) {
                        if (_self.positions.length < 4) {
                            return;
                        }
                        // remove the point and the corresponding markers
                        _self.positions.splice(index, 1);
                        _self._createPrimitive = true;
                        markers.removeBillboard(index);
                        editMarkers.removeBillboard(index);
                        updateHalfMarkers(index, _self.positions);
                        onEdited();
                    },
                    tooltip: function () {
                        if (_self.positions.length > 3) {
                            return "双击移除结点";
                        }
                    }
                };
                markers.addBillboards(_self.positions, handleMarkerChanges);
                this._markers = markers;
            }
        }
    }
}
```



