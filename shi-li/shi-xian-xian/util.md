#### 实现线中的一些辅助方法

##### cloneObjDraw

克隆对象

```
function cloneObjDraw(from, to) {
    if (from == null || typeof from != "object") return from;
    if (from.constructor != Object && from.constructor != Array) return from;
    if (from.constructor == Date || from.constructor == RegExp || from.constructor == Function ||
        from.constructor == String || from.constructor == Number || from.constructor == Boolean)
        return new from.constructor(from);

    to = to || new from.constructor();

    for (var name in from) {
        to[name] = typeof to[name] == "undefined" ? cloneObjDraw(from[name], null) : to[name];
    }

    return to;
}
```

##### copyOptionsDraw

返回defaultOptions和options的合并对象

```
function copyOptionsDraw(options, defaultOptions) {
    var newOptions = cloneObjDraw(options), option;
    for (option in defaultOptions) {
        if (newOptions[option] === undefined) {
            newOptions[option] = cloneObjDraw(defaultOptions[option]);
        }
    }
    return newOptions;
}
```

##### fillOptionsDraw

克隆defaultOptions到options中

```
function fillOptionsDraw(options, defaultOptions) {
    options = options || {};
    var option;
    for (option in defaultOptions) {
        if (options[option] === undefined) {
            options[option] = cloneObjDraw(defaultOptions[option]);
        }
    }
}
```

##### getDisplayLatLngString

获取经纬度

```
function getDisplayLatLngString(cartographic, precision) {
    return Cesium.Math.toDegrees(cartographic.longitude).toFixed(precision || 3) + ", " + Cesium.Math.toDegrees(cartographic.latitude).toFixed(precision || 3);
}
```



