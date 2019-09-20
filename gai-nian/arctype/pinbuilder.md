# PinBuilder

用于生成自定义地图引脚作为画布元素的实用程序类

#### 方法

#### fromColor {#fromColor}

fromColor\(color, size\) → Canvas

创建指定颜色和大小的空针。

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| `color` | [颜色](https://cesiumjs.org/Cesium/Build/Documentation/Color.html) | 针的颜色。 |
| `size` | 数 | 引脚的大小，以像素为单位。 |

```
billboard = {
    image: pinBuilder.fromColor(Cesium.Color.ROYALBLUE, 48).toDataURL(),
}
```

#### fromText {#fromText}

fromText\(text, color, size\) → Canvas

创建具有指定文本，颜色和大小的图钉。文本的大小将尽可能大，同时仍然完全包含在引脚内。

```
billboard = {
    image: pinBuilder.fromText('?', Cesium.Color.BLACK, 48).toDataURL(),
}
```

#### fromMakiIconId {#fromMakiIconId}

fromMakiIconId\(id, color, size\) → Canvas\|Promise.&lt;Canvas&gt;

创建具有指定maki图标标识符，颜色和大小的图钉。

```
var hospitalPin = Cesium.when(pinBuilder.fromMakiIconId('hospital', Cesium.Color.RED, 48), function(canvas) {
    return viewer.entities.add({
        name : 'Hospital',
        position : Cesium.Cartesian3.fromDegrees(-75.1698606, 39.9211275),
        billboard : {
            image : canvas.toDataURL(),
            verticalOrigin : Cesium.VerticalOrigin.BOTTOM
        }
    });
});
```



