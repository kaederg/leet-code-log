# Initial Solution

Exhaust matching str to exp from left to right.

```
function starTest(str, exp) {
    if(str == "" && exp == "") return true;
    if(exp == "" && str != "") return false;
    if(str == "" && exp.length == 2 && exp[0] != '*' && exp[1] == '*') return true;

    var str_i = 0;
    var exp_i = 0;
    while(exp[exp_i] != '*') {
        if(str_i < str.length && (str[str_i] == exp[exp_i] || exp[exp_i] == '.')) {
            str_i++;
            exp_i++;     
        }
        else {
            if(exp_i + 1 < exp.length && exp[exp_i + 1] == "*") {
                exp_i += 2;
            }
            else {
                return false;                
            }
        }
        
        if(str_i == str.length && exp_i == exp.length) {
            return true;
        }
        if(str_i != str.length && exp_i == exp.length) {
            return false;
        }
    }
    
    if(str_i > 0 && exp_i + 1 < exp.length && starTest(str.slice(str_i - 1), exp.slice(exp_i + 1))) {
        return true;
    }
    //going forward
    var exp_ref = exp[exp_i - 1];
    var exp_new = exp.slice(exp_i + 1);
    //console.log(exp_ref);
    //console.log(exp_new);
    while(str[str_i] == exp_ref || exp_ref == '.') {
        if(starTest(str.slice(str_i), exp_new)) {
            return true;
        }
        else {
            str_i++;
            if(str_i >= str.length) {
                break;
            }
        }
    }
    
    return starTest(str.slice(str_i), exp_new);
}

var isMatch = function(s, p) {
    return starTest(s, p);
};
```
