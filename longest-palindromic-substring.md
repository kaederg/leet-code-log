# Initial Solution - Expand Around Center

```
var longestPalindrome = function(s) {
    var result = "";
    var curr = "";
    for(var i = 0; i < s.length; i++) {
        //even palindromic
        if(i+1 < s.length && s[i] == s[i+1]) {
            curr = s[i] + s[i+1];
            if(curr.length > result.length) {
                result = curr;
            }
            for(var j = 1; j <= i; j++) {
                if(i + 1 + j <= s.length - 1 && i-j >=0 && s[i+1+j] == s[i-j]) {
                    curr = s[i + 1 + j] + curr + s[i - j];
                    //console.log('i:'+i+' j:'+j+' curr:'+curr);
                }
                else {
                    break;
                }
                if(curr.length > result.length) {
                    result = curr;
                }
            }
            curr = "";
        }
        
        //odd palindromic
        curr = s[i];
        if(curr.length > result.length) {
            result = curr;
        }
        for(var j = 1; j <= i; j++) {
            if(i + j <= s.length - 1 && i-j >=0 && s[i+j] == s[i-j]) {
                curr = s[i + j] + curr + s[i - j];
                //console.log('i:'+i+' j:'+j+' curr:'+curr);
            }
            else {
                break;
            }
            if(curr.length > result.length) {
                result = curr;
            }
        }
        curr = "";
    }   
    return result;
};
```

# Manacher's algorithm

Manacher's algorithm solves two issues that slows down the process

1. parity

Padding the string with same character in between every two characters ensures the original string length even and keep its palindromicity.

2. repeated verification

Introducing an array (R) to store radius of local palindromic string

|i	|0|	1|	2|	3|	4|	5|	6|	7|	8|	9| 10|	11|	12|	13|	14|	15|	16|	17|	18|	
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|T[i]|	#|	a|	#|	a|	#|	b|	#|	a|	#|	h|	#|	o|	#|p  |	#|	x|	#	|p	|#|
|R[i]|	1|	2|	3|	2|	1|	4|1	 |2  |	1|	2|	1|	2|1  |	2|	1|	4|1	    |2	|1|

The key to solve for R in O(l) is reuse the information in previously found palindromic strings.

Still applying expand around center process from left to right. 
1. i = 0, R[0] = 1, palindromic string = "#". 
2. i = 1, R[1] = 2, palindromic string = "#a#".
3. i = 2, R[2] = 3, palindromic string = "#a#a#"
4. i = 3, based on algo implementation, this step seems suffice the conditions that dun need to solve, but because it is a boundary condition, it actually requires solving to make sure extending sequence.

