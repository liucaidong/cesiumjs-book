* ## drwaPlot.js

```
var arrow = {
    isActivate: false, //是否激活状态
    drawArr: [],
    handler: null,
    viewer: null,
    init: function(){},
    disable： function(){},
    draw: function(){},
}
```

#### 方法

| init | 初始化 |
| :--- | :--- |
| disable | 销毁 |

##### draw -开始绘制

* 声明对应的路径绘制对象

```
draw: function(type) {
    switch (type) {
        case "straightArrow":
            var straightArrow = new StraightArrow(viewer);
            straightArrow.startDraw();
            this.drawArr.push(straightArrow);
            break;
        case "attackArrow":
            var attackArrow = new AttackArrow(viewer);
            attackArrow.startDraw();
            this.drawArr.push(attackArrow);
            break;
        case "pincerArrow":
            var pincerArrow = new PincerArrow(viewer);
            pincerArrow.startDraw();
            this.drawArr.push(pincerArrow);
        default:
            break;
    }
},
```

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

##### disable -销毁方法

* 将drawArr handler viewer 等变量销毁

```
disable: function() {
    if (this.isActivate) {
        this.isActivate = false;
        for (var i = 0; i < this.drawArr.length; i++) {
            this.drawArr[i].disable();
        }
        this.drawArr = [];
        if (this.handler) {
            this.handler.destroy();
            this.handler = null;
        }
        this.viewer = null;
    }
},
```



