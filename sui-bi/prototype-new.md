#### .prototype = new obj\(\);

功能相当于继承

##### 实例：

```
function animal() {
    this.name = null;
}

animal.prototype.say = function () {
    console.log(this.name);
}

function cat(name) {
    this.name = name;
}

cat.prototype = new animal();

var c = new cat("喵");
c.say(); //喵
```



