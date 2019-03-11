# In-Place

```
var sortArrayByParity = function(A) {
    var i = 0, j = A.length - 1;
    while(j > i) {
        //console.log(A);
        var bi = A[i]%2 == 0;
        var bj = A[j]%2 == 0;
        if(bj && !bi) {
            var tmp = A[j];
            A[j] = A[i];
            A[i] = tmp;
            i++;
            j--;  
        }
        else if(!bi && !bj) {
            j--;
        }
        else if(bi && bj) {
            i++;
        }
        else {
            i++;
            j--;            
        }
    }
    return A;
};
```
