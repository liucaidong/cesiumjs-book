## Cesium.Color.fromRandom\(options, result\) → Color

使用提供的选项创建随机颜色。对于可重现的随机颜色，应CesiumMath\#setRandomNumberSeed在应用程序开始时调用一次。

```
//创建完全随机的颜色
var color = Cesium.Color.fromRandom();

//创建一个随机的黄色阴影。
var color = Cesium.Color.fromRandom({
    red : 1.0,
    green : 1.0,
    alpha : 1.0
});
```



