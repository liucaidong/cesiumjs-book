## new Cesium.Material\(options\)

材质通过漫反射，镜面反射，法线，发射和alpha分量的组合来定义表面外观。

这些值是使用名为Fabric的JSON模式指定的，该模式在幕后被解析并组装成glsl着色器代码。

* 翻译：材料

#### 例子：

```
// Create a color material with fromType:
polygon.material = Cesium.Material.fromType('Color');
polygon.material.uniforms.color = new Cesium.Color(1.0, 1.0, 0.0, 1.0);

// Create the default material:
polygon.material = new Cesium.Material();

// Create a color material with full Fabric notation:
polygon.material = new Cesium.Material({
    fabric : {
        type : 'Color',
        uniforms : {
            color : new Cesium.Color(1.0, 1.0, 0.0, 1.0)
        }
    }
});
```



