```
var maxArea = function(height) {
    var max = 0;
    var i = 0, j = height.length - 1, ref;
    while(j > i) {
        if(height[i] > height[j]) {
            ref = height[j];
            j--;
        }
        else {
            ref = height[i];
            i++;
        }
        var curr = ref * (j - i + 1);
        if(curr > max) max = curr;
    }
    return max;
};
```
