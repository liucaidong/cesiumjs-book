## PolylinePrimitive

折线实体类

```
PolylinePrimitive = (function () {}(
    var materialLine = Cesium.Material.fromType(Cesium.Material.ColorType);
    materialLine.uniforms.color = new Cesium.Color(1.0, 1.0, 0.0, 0.5);

    //线的属性
    var defaultShapeOptions = {
        ellipsoid: Cesium.Ellipsoid.WGS84,
        textureRotationAngle: 0.0,
        height: 0.0,
        asynchronous: true,
        show: true,
        debugShowBoundingVolume: false
    };
    var defaultPolylineOptions = copyOptionsDraw(defaultShapeOptions, {
        width: 5,
        geodesic: true,
        granularity: 10000,
        appearance: new Cesium.PolylineMaterialAppearance({
            aboveGround: false
        }),
        material: materialLine
    });

    function _(options) {
        options = copyOptionsDraw(options, defaultPolylineOptions);

        this.initialiseOptions(options);
    }

     _.prototype = new ChangeablePrimitive(); //?? 继承

     //设置方法
     _.prototype.setPositions = function (positions) {
        this.setAttribute('positions', positions);
     };
     _.prototype.setWidth = function (width) {
        this.setAttribute('width', width);
     };
     _.prototype.setGeodesic = function (geodesic) {
     this.setAttribute('geodesic', geodesic);
     };
     //获取方法
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

)());
```



