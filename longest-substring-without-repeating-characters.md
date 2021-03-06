# Hash Object

`console.log` eats quite a lot of memory and time

```
var lengthOfLongestSubstring = function(s) {
    var hash = {};
    var start = 0;
    var result = 0;
    for(var i = 0; i < s.length; i++) {
        if(typeof hash[s[i]] != 'undefined') {
            if(result < i - start) {
                result = i - start;
                //console.log('i:'+i+'s:'+start);
            }
            if(start < hash[s[i]] + 1) {
                start = hash[s[i]] + 1;                
            }
        }
        hash[s[i]] = i;
    }
    if(s.length - start > result) {
        result = s.length - start;
        //console.log('i:'+s.length+'s:'+start);
    }
    return result;
};
```

Performance

| Runtime | Memory  |
|---      |---      |
| 112 ms  | 40.6 MB |


# Sliding Window

```
var lengthOfLongestSubstring = function(s) {
    var slider = "";
    var result = 0;
    for(var j = 0; j < s.length; j++) {
        var i = slider.indexOf(s[j]);
        if(i < 0) {
            slider += s[j];
            if(slider.length > result) {
                result = slider.length;
            }
        }
        else {
            slider = slider.slice(i + 1, slider.length);
            slider += s[j];
        }
    }
    return result;
};
```

Performance 

| Runtime | Memory  |
|---      |---      |
| 96 ms  | 40.3 MB |


# `substring` and `slice` and `substr`

Short answer is `slice` is the implementation with the least unexpected behaviour.

`str.slice(beginIndex[, endIndex])`
