Runtime: 84 ms, faster than 58.39% of JavaScript online submissions for String to Integer (atoi).

Memory Usage: 36.2 MB, less than 48.96% of JavaScript online submissions for String to Integer (atoi).

Performance is not well optimized.

```
var myAtoi = function(str) {
    var result = null;
    var plus = null;
    var max = Math.pow(2, 31);
    //str = str.trim();
    for(var i = 0; i < str.length; i++) {
        //console.log(str[i])
        var code = str.charCodeAt(i);
        if(code < 48  || code > 57) {
            if (plus == null && result == null) {
                if(code == 32) {
                    continue;
                }
                else if(code == 45) {
                    plus = -1;
                    continue;
                }
                else if(code == 43) {
                    plus = 1;
                    continue;
                }
            }
            break;
        }
        result = result * 10 + code - 48;
        //console.log(result);
        if(result >= max) {
            return plus == -1 ? max * -1 : max - 1;
        }
    }
    return plus == -1 ? result * -1 : result;
};
```
