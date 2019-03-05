More like a math riddle

```
var convert = function(s, numRows) {
    if(numRows == 1) return s;
    
    var result = "";
    var npb = numRows*2 - 2;
    var leftover = s.length % npb;
    var fullc = (s.length - leftover)/npb;
    
    for(var i = 0; i< numRows; i++) {
        for(var j=0; j<fullc+1;j++) {
            if(i==0) {
                if(j >= fullc && leftover==0) {
                    break;
                }
                result += s[i + npb*j];
                
            }
            else if(i == numRows - 1) {
                if(j >= fullc && leftover<numRows) {
                    break;
                }
                result += s[i + npb*j];                 
            }
            else {
                if(j >= fullc && leftover<=i) {
                    break;
                }
                result += s[i + npb*j];
                if(j >= fullc && leftover<numRows*2 - i - 1) {
                    break;
                }
                result += s[i + (numRows - i - 1)*2 + npb*j];
            }
        }
    }
    
    return result;
};
```
