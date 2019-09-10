## 绘制广告牌

```
var billboards = viewer.scene.primitives.add(new Cesium.BillboardCollection());
billboards.add({
    show: true,
    position: cartesian,
    scale: 1.0,
    image: images[type],
    color: opt["center-color"],
    width: opt.size,
    height: opt.size
});
```



