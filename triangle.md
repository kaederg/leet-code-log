
```
var minimumTotal = function(triangle) {
    if (triangle.length == 0) return 0;
    for(var i = triangle.length - 2; i >= 0; i--) {
        for(var j = 0; j < triangle[i].length; j++) {
            triangle[i][j] += triangle[i+1][j] > triangle[i+1][j+1] ? triangle[i+1][j+1] : triangle[i+1][j];
        }
        //console.log(row);
    }
    return triangle[0][0];
};
```
