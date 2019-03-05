A good improvement in efficiency is actually ensure x to be positive and compare only with max.

```
var reverse = function(x) {
    var result = 0;
    var max = Math.pow(2, 31) - 1;
    var plus = x > 0;
    x = plus ? x : (x * (-1));
    if(x > max) return 0;
    while(x > 0) {
        var tmp = x%10;
        result = result * 10 + tmp;
        x = (x-tmp)/10;
    }
    if(result > max) return 0;
    return plus ? result : (result * (-1));
};
```
