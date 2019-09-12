## js调试 - debugger

在代码中加入一行 - debugger;

* 调试过程中会下实处变量的值等等信息，这样在找bug的过程中就会方便的多。

```

```

---

```
addListener事件监听
```

addListener是用于鼠标，键盘等特殊元素的一些监听

addEventListener是对组件监听的

```
var btn = document.getElementById("btn");
btn.addEventListener("click",function () {
    console.log("click");
});
```

# js判断数组中是否存在某个值

```
$.inArray(item,items) == -1
```

```
items.indexOf(item) == -1
```

注意类型

