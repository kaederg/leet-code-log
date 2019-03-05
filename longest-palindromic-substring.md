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

Introducing an array (r) to store radius of local palindromic string

|i	|0|	1|	2|	3|	4|	5|	6|	7|	8|	9| 10|	11|	12|	13|	14|	15|	16|	17|	18|	19|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|s_new[i]|	$|	#|	a|	#|	b|	#|	b|	#|	a|	#|	h|	#|	o|	#	|p|	#|	x|	#	|p	|#|
|r[i]	|	1|	2|	1|	2|	5|	2	|1	|2|	1|	2|	1|	2	|1|	2|	1|	4	|1	|2	|1|

Solve for r in O(l).
