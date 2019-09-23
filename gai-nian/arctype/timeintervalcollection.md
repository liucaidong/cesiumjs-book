# TimeIntervalCollection

A non-overlapping collection of TimeInterval instances sorted by start time.

按开始时间排序的 时间间隔实例 的非重叠集合。

# TimeInterval

new Cesium.TimeInterval\(options\)

由开始和停止时间定义的时间间隔；（可选）将这些时间包括在间隔中。可以选择将任意数据与每个实例相关联，

```
//创建一个跨越1980年8月1日且关联的实例
//使用笛卡尔位置。
var timeInterval = new Cesium.TimeInterval({
    start : Cesium.JulianDate.fromIso8601('1980-08-01T00:00:00Z'),
    stop : Cesium.JulianDate.fromIso8601('1980-08-02T00:00:00Z'),
    isStartIncluded : true,
    isStopIncluded : false,
    data : Cesium.Cartesian3.fromDegrees(39.921037, -75.170082)
});
```



