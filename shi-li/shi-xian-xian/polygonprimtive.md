## PolygonPrimitive

多边形实体类

```
PolygonPrimitive = (function () {}(
    var materialSurface = Cesium.Material.fromType(Cesium.Material.ColorType);
    materialSurface.uniforms.color = new Cesium.Color(0.0, 1.0, 1.0, 0.5);
    var defaultShapeOptions = {
      ellipsoid: Cesium.Ellipsoid.WGS84,
      textureRotationAngle: 0.0,
      height: 0.0,
      asynchronous: true,
      show: true,
      debugShowBoundingVolume: false
    };
    var defaultSurfaceOptions = copyOptionsDraw(defaultShapeOptions, {
        appearance: new Cesium.EllipsoidSurfaceAppearance({
            aboveGround: false
        }),
        material: materialSurface,
        granularity: Math.PI / 180.0
    });
    var defaultPolygonOptions = copyOptionsDraw(defaultSurfaceOptions, {});
    function _(options) {
        options = copyOptionsDraw(options, defaultPolygonOptions);
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
));
```



