## drwaPlot.js

```
var arrow = {
    isActivate: false,
    drawArr: [],
    handler: null,
    viewer: null,
    init: function(){},

}
```

##### init

* 设置参数isActivate,viewer
* 执行this.bindEdit\(\)

```
init: function(viewer) {
    if (!this.isActivate) {
        this.isActivate = true;
        this.viewer = viewer;
        this.bindEdit();
    }
},
```



