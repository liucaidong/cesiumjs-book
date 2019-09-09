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
      
}
```



