#hashtable

trade space for speed

- two-pass: build hashtable on first run, get results on second run
- one-pass: look for results while building hashtable

javascript hashtable implementation 

with Map
```
var twoSum = function(nums, target) {
    let map = new Map;
    for (var i = 0; i < nums.length; i++) {
        let complement = target - nums[i];
        if (map.has(complement)) {
            return [map.get(complement), i]
        }
        map.set(nums[i], i);
    }
}
```
performance
| Runtime | Memory |
|---------|--------|
| 88 ms	  | 35.1 MB|


with object
```
var twoSum = function(nums, target) {
    var hash = {};
    var result = [];
    for (var i = 0; i< nums.length; i++) {
        if(typeof hash[nums[i]] == 'undefined') {
            hash[nums[i]] = i;            
        }
        result.push(i);
        var test = target - nums[i];
        if(typeof hash[test] != 'undefined' && hash[test] != i) {
            result.push(hash[test]);
            return result;
        }
        result.pop();
    }
    return result;
};
```
performance
| Runtime | Memory  |
|---------|---------|
| 64 ms	  | 36.7 MB |
