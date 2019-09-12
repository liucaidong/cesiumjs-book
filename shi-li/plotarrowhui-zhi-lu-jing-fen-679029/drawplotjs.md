## drwaPlot.js

```
var arrow = {
    isActivate: false, //是否激活状态
    drawArr: [],
    handler: null,
    viewer: null,
    init: function(){},
    disable： function(){},

}
```

#### 方法

| init | 初始化方法 |
| :--- | :--- |
| disable |  |

##### init -初始化方法

* 设置参数 isActivate,viewer
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

##### disable

```

```

