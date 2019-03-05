# Initial Solution

```
var findMedianSortedArrays = function(nums1, nums2) {
    var total = nums1.length + nums2.length;
    var half = Math.floor(total/2);
    var odd = total%2;
    
    var count = 0;
    var i1 = 0, i2 = 0;
    var curr = 0;
    
    while(i1 < nums1.length || i2 < nums2.length) {
        if(i1 >= nums1.length || nums1[i1] >= nums2[i2]) {  //careful with index boundary check
            if(count == half && odd == 0) {
                return (curr+nums2[i2])/2
            }
            curr = nums2[i2];
            i2++;
        }
        else {
            if(count == half && odd == 0) {
                return (curr+nums1[i1])/2
            }
            curr = nums1[i1];
            i1++;
        }
        count++;
        if(count == half + 1 && odd == 1) {
            return curr;
        }
    }
};
```

# Optimized Approach

This sorting process consistently runs (m+n+1)/2 times to get to the median from the start of the array. An optimized approach could run from some estimated middle point, where (m+n+1)/2 is the worst case scenario.

For nums1: A, nums2: B, after the adjustment completed, we should have found i and j such that for A0, ..., Ai-1, Ai, Ai+1, ...Am and B0, ..., Bj-1, Bj, Bj+1, ...Bn, 

1. Ai<Bj+1 and Bj<Ai+1
2. i + j = (m+n)/2

If m+n is odd, take min(Ai, Bj)

Boundary cases for comparing with first and last elements are quite tedious to list. 
