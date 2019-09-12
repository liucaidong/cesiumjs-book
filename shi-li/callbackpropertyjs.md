## **CallbackProperty.js** {#blob-path}

```
define([],function(...){
    'use strict';

    function CallbackProperty(callback,isConstant){}

    defineProperties();

    CallbackProperty.prototype.getValue = function(time,result){}
});
```

##### getValue

```
CallbackProperty.prototype.getValue = function(time, result) {
    return this._callback(time, result);
};
```

##### defineProperties

```
defineProperties(CallbackProperty.prototype, {
    /**
     * Gets a value indicating if this property is constant.
     * @memberof CallbackProperty.prototype
     *
     * @type {Boolean}
     * @readonly
     */
    isConstant : {
        get : function() {
            return this._isConstant;
        }
    },
    /**
     * Gets the event that is raised whenever the definition of this property changes.
     * The definition is changed whenever setCallback is called.
     * @memberof CallbackProperty.prototype
     *
     * @type {Event}
     * @readonly
     */
    definitionChanged : {
        get : function() {
            return this._definitionChanged;
        }
    }
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



