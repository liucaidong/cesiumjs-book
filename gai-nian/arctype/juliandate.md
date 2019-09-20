# JulianDate

代表天文朱利安日期，即自-4712年（公元前4713年）1月1日中午以来的天数。为了提高精度，此类将日期的整数部分和日期的秒部分存储在单独的组件中。为了安全算术并表示闰秒，日期始终存储在国际原子时标准中 TimeStandard.TAI。

| 名称 | 类型 | 默认 | 描述 |
| :--- | :--- | :--- | :--- |
| `julianDayNumber` | 数 | `0.0` | 可选的朱利安日数字代表整天的数量。分数天也将正确处理。 |
| `secondsOfDay` | 数 | `0.0` | optional当前Julian Day Number的秒数。将正确处理大于一天的小数秒，负秒和秒。 |
| `timeStandard` | [TimeStandard](https://cesiumjs.org/Cesium/Build/Documentation/TimeStandard.html) | `TimeStandard.UTC` | optional定义前两个参数的时间标准。 |

#### 注意

1. viewer.clock.shouldAnimate = true;  必须

#### 方法

#### secondsDifference {#.secondsDifference}

Cesium.JulianDate.secondsDifference\(left, right\) → Number

计算提供的实例之间的秒数差异。

```
Cesium.JulianDate.secondsDifference(time, startTime);
```

#### now {#.now}

Cesium.JulianDate.now （result） → JulianDate

创建表示当前系统时间的新实例

```
var startTime = Cesium.JulianDate.now();
```



