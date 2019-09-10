## Cesium.Entity

实体实例将多种形式的可视化聚合到单个高级对象中。

| 名称 | 类型 | 描述 |
| :--- | :--- | :--- |
| `id` | 串 | optional此对象的唯一标识符。如果未提供，则生成GUID。 |
| `name` | 串 | 可选显示给用户的可读名称。它不一定是唯一的。 |
| `availability` | [TimeIntervalCollection](https://cesiumjs.org/Cesium/Build/Documentation/TimeIntervalCollection.html) | 可选与此对象关联的可用性（如果有）。 |
| `show` | 布尔 | optional一个布尔值，指示是否显示实体及其子项。 |
| `description` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | optional一个字符串属性，指定此实体的HTML描述。 |
| `position` | [PositionProperty](https://cesiumjs.org/Cesium/Build/Documentation/PositionProperty.html) | optional一个指定实体位置的属性。 |
| `orientation` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | optional一个指定实体方向的属性。 |
| `viewFrom` | [属性](https://cesiumjs.org/Cesium/Build/Documentation/Property.html) | 可选用于查看此对象的建议初始偏移量。 |
| `parent` | [实体](https://cesiumjs.org/Cesium/Build/Documentation/Entity.html) | 可选与此实体关联的父实体。 |
| `billboard` | [BillboardGraphics](https://cesiumjs.org/Cesium/Build/Documentation/BillboardGraphics.html) | 可选与此实体关联的广告牌。 |
| `box` | [BoxGraphics](https://cesiumjs.org/Cesium/Build/Documentation/BoxGraphics.html) | 可选与此实体关联的框。 |
| `corridor` | [CorridorGraphics](https://cesiumjs.org/Cesium/Build/Documentation/CorridorGraphics.html) | 可选与此实体关联的走廊。 |
| `cylinder` | [CylinderGraphics](https://cesiumjs.org/Cesium/Build/Documentation/CylinderGraphics.html) | 可选与此实体关联的柱面。 |
| `ellipse` | [EllipseGraphics](https://cesiumjs.org/Cesium/Build/Documentation/EllipseGraphics.html) | 可选与该实体关联的椭圆。 |
| `ellipsoid` | [EllipsoidGraphics](https://cesiumjs.org/Cesium/Build/Documentation/EllipsoidGraphics.html) | 可选与此实体关联的椭圆体。 |
| `label` | [LabelGraphics](https://cesiumjs.org/Cesium/Build/Documentation/LabelGraphics.html) | optionalA options.label与此实体关联。 |
| `model` | [ModelGraphics](https://cesiumjs.org/Cesium/Build/Documentation/ModelGraphics.html) | 可选与此实体关联的模型。 |
| `path` | [PathGraphics](https://cesiumjs.org/Cesium/Build/Documentation/PathGraphics.html) | 可选与此实体关联的路径。 |
| `plane` | [PlaneGraphics](https://cesiumjs.org/Cesium/Build/Documentation/PlaneGraphics.html) | 可选与此实体关联的平面。 |
| `point` | [PointGraphics](https://cesiumjs.org/Cesium/Build/Documentation/PointGraphics.html) | 可选与此实体关联的点。 |
| `polygon` | [PolygonGraphics](https://cesiumjs.org/Cesium/Build/Documentation/PolygonGraphics.html) | 可选与此实体关联的多边形。 |
| `polyline` | [PolylineGraphics](https://cesiumjs.org/Cesium/Build/Documentation/PolylineGraphics.html) | 可选与此实体关联的折线。 |
| `properties` | [属性包](https://cesiumjs.org/Cesium/Build/Documentation/PropertyBag.html) | 可选的与此实体关联的任意属性。 |
| `polylineVolume` | [PolylineVolumeGraphics](https://cesiumjs.org/Cesium/Build/Documentation/PolylineVolumeGraphics.html) | optional与此实体关联的polylineVolume。 |
| `rectangle` | [RectangleGraphics](https://cesiumjs.org/Cesium/Build/Documentation/RectangleGraphics.html) | 可选与此实体关联的矩形。 |
| `wall` | [WallGraphics](https://cesiumjs.org/Cesium/Build/Documentation/WallGraphics.html) | 可选与此实体关联的墙。 |



