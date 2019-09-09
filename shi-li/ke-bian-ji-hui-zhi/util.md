##### setListener

设置监听

```
function setListener(primitive, type, callback) {
    primitive[type] = callback;
}
```

##### muteHandlers

取消

```
_.prototype.muteHandlers = function (muted) {
    this._handlersMuted = muted;
};
```

##### enhanceWithListeners

```
function enhanceWithListeners(element) {
    element._listeners = {};

    element.addListener = function (name, callback) {
        this._listeners[name] = (this._listeners[name] || []);
        this._listeners[name].push(callback);
        return this._listeners[name].length;
    };
    //注册事件
    element.executeListeners = function (event, defaultCallback) {
        if (this._listeners[event.name] && this._listeners[event.name].length > 0) {
            var index = 0;
            for (; index < this._listeners[event.name].length; index++) {
                this._listeners[event.name][index](event);
            }
        } else {
            if (defaultCallback) {
                defaultCallback(event);
            }
        }
    }
}
```

##### disableAllHighlights

确保只有一个对象处于高亮

```
_.prototype.disableAllHighlights = function () {
    this.setHighlighted(undefined);
};
 _.prototype.setHighlighted = function (surface) {
    if (this._highlightedSurface && !this._highlightedSurface.isDestroyed() && this._highlightedSurface != surface) {
        this._highlightedSurface.setHighlighted(false);
    }
    this._highlightedSurface = surface;
};
```

##### setEdited

设置编辑状态

```
_.prototype.setEdited = function (surface) {
    if (this._editedSurface && !this._editedSurface.isDestroyed()) {
        this._editedSurface.setEditMode(false);
    }
    this._editedSurface = surface;
};
```



