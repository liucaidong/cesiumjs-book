## **CallbackProperty.js** {#blob-path}

```
define([],function(...){
    'use strict';

    function CallbackProperty(callback,isConstant){}
});
```

##### CallbackProperty

```
function CallbackProperty(callback, isConstant) {
    this._callback = undefined;
    this._isConstant = undefined;
    this._definitionChanged = new Event();
    this.setCallback(callback, isConstant);
}
```

##### ...

```
defined,
defineProperties,
DeveloperError,
Event
```

##### \[\]

```
'../Core/defined',
'../Core/defineProperties',
'../Core/DeveloperError',
'../Core/Event'
```



