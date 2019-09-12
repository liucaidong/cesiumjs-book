## **CallbackProperty.js** {#blob-path}

```
define([],function(...){
    'use strict';

    function CallbackProperty(callback,isConstant){}

    defineProperties();

    CallbackProperty.prototype.getValue = function(time,result){}

    CallbackProperty.prototype.setCallback =function(callback,isConstant);

    CallbackProperty.prototype.equals = function(other){}
    
    return CallbackProperty;
});
```

##### equals

```
CallbackProperty.prototype.equals = function(other) {
    return this === other || (other instanceof CallbackProperty && this._callback === other._callback && this._isConstant === other._isConstant);
};
```

##### setCallback

```
CallbackProperty.prototype.setCallback = function(callback, isConstant) {
    //>>includeStart('debug', pragmas.debug);
    if (!defined(callback)) {
        throw new DeveloperError('callback is required.');
    }
    if (!defined(isConstant)) {
        throw new DeveloperError('isConstant is required.');
    }
    //>>includeEnd('debug');

    var changed = this._callback !== callback || this._isConstant !== isConstant;

    this._callback = callback;
    this._isConstant = isConstant;

    if (changed) {
        this._definitionChanged.raiseEvent(this);
    }
};
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



