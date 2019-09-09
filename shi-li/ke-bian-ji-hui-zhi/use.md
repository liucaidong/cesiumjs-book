#### 多段线

PolylinePrimitive

```
_.PolylinePrimitive = (function () {
    function _(options, viewer) {
        if (isCreat) { } else {
            new ChangeablePrimitiveTool(viewer);
        }
        options = copyOptions(options, defaultPolylineOptions);

        this.initialiseOptions(options);
    }
    _.prototype = new ChangeablePrimitive();
    _.prototype.setPositions = function (positions) {
        this.setAttribute('positions', positions);
    };
    _.prototype.setWidth = function (width) {
        this.setAttribute('width', width);
    };
    _.prototype.setGeodesic = function (geodesic) {
        this.setAttribute('geodesic', geodesic);
    };
    _.prototype.getPositions = function () {
        return this.getAttribute('positions');
    };
    _.prototype.getWidth = function () {
        return this.getAttribute('width');
    };
    _.prototype.getGeodesic = function (geodesic) {
        return this.getAttribute('geodesic');
    };
    _.prototype.getGeometry = function () {
        if (!Cesium.defined(this.positions) || this.positions.length < 2) {
            return;
        }
        return new Cesium.PolylineGeometry({
            positions: this.positions,
            height: this.height,
            width: this.width < 1 ? 1 : this.width,
            vertexFormat: Cesium.EllipsoidSurfaceAppearance.VERTEX_FORMAT,
            ellipsoid: this.ellipsoid
        });
    };
    return _;
})();
```

#### 多边形

PolygonPrimitive

```
_.PolygonPrimitive = (function () {
    function _(options) {
        if (isCreat) { } else {
            new ChangeablePrimitiveTool(viewer);
        }
        options = copyOptions(options, defaultPolygonOptions);
        this.initialiseOptions(options);
        this.isPolygon = true;
    }

    _.prototype = new ChangeablePrimitive();//继承
    _.prototype.setPositions = function (positions) {
        this.setAttribute('positions', positions);
    };
    _.prototype.getPositions = function () {
        return this.getAttribute('positions');
    };
    _.prototype.getGeometry = function () {
        if (!Cesium.defined(this.positions) || this.positions.length < 3) {
            return;
        }
        return Cesium.PolygonGeometry.fromPositions({
            positions: this.positions,
            height: this.height,
            vertexFormat: Cesium.EllipsoidSurfaceAppearance.VERTEX_FORMAT,
            stRotation: this.textureRotationAngle,
            ellipsoid: this.ellipsoid,
            granularity: this.granularity
        });
    };

    _.prototype.getOutlineGeometry = function () {
        return Cesium.PolygonOutlineGeometry.fromPositions({
            positions: this.getPositions()
        });
    };
    return _;
})();
```



