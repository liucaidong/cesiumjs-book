## drwaPlot.js

```
var arrow = {
    isActivate: false,
    drawArr: [],
    handler: null,
    viewer: null,
    init: function(){},

}
```

##### init

```
init: function(viewer) {
	if (!this.isActivate) {
		this.isActivate = true;
		this.viewer = viewer;
		this.bindEdit();
	}
},
```



