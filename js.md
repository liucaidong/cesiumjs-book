## js调试 - debugger

在代码中加入一行 - debugger;

* 调试过程中会下实处变量的值等等信息，这样在找bug的过程中就会方便的多。

```
bindEdit: function() {
	var $this = this;
	this.handler = new Cesium.ScreenSpaceEventHandler(this.viewer.scene.canvas);
	this.handler.setInputAction(function(evt) { //单机开始绘制
		var pick = $this.viewer.scene.pick(evt.position);
		debugger;
		if (Cesium.defined(pick) && pick.id) {
			if ($this.nowArrowObj) {
				if ($this.nowArrowObj.state != -1) {
					console.log("上一步操作未结束，请继续完成上一步！");
					return;
				}
			}
			for (var i = 0; i < $this.drawArr.length; i++) {
				if (pick.id.objId == $this.drawArr[i].objId) {
					$this.nowArrowObj = $this.drawArr[i];
					$this.drawArr[i].startModify();
					break;
				}
			}
		}
	}, Cesium.ScreenSpaceEventType.LEFT_CLICK);
},
```

---

```
addListener事件监听
```

addListener是用于鼠标，键盘等特殊元素的一些监听

addEventListener是对组件监听的

```
var btn = document.getElementById("btn");
btn.addEventListener("click",function () {
    console.log("click");
});
```

# js判断数组中是否存在某个值

```
$.inArray(item,items) == -1
```

```
items.indexOf(item) == -1
```

注意类型

