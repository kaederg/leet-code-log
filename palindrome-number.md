# Initial Solution

```
var isPalindrome = function(x) {
    if(x < 0) return false;
    if(x == 0) return true;
    
    var tmp = 0, ref = x;
    while(x > 0) {
        tmp = tmp*10 + x%10;
        x = Math.floor(x/10);
    }
    return tmp == ref;
};
```

|   Runtime |   Memory  |
|---        |---        |
|   236 ms  |   45.2 MB |

# Improved Solution

```
var isPalindrome = function(x) {
    if(x < 0) return false;
    if(x == 0) return true;
    if(x%10 == 0) return false; //observation
    
    var tmp = 0; //only need to run to the middle digit
    while(x > tmp) {
        tmp = tmp*10 + x%10;
        x = Math.floor(x/10);
    }
    return tmp == x || x == Math.floor(tmp/10); //or for the odd number of digits
};
```
Perfomance not improved though.

|   Runtime |   Memory  |
|---        |---        |
|   232 ms  |   45.2 MB |
