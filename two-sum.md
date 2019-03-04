# hashtable

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

| Runtime | Memory  |
| ------- | ------- |
| 88 ms	  | 35.1 MB |


with object
```
var twoSum = function(nums, target) {
    let hash = new Object;
    for (var i = 0; i< nums.length; i++) {
        var complement = target - nums[i];
        if(!isNaN(Number(hash[complement]))) {
            return [i, hash[complement]];
        }
        if(isNaN(Number(hash[nums[i]]))) {
            hash[nums[i]] = i;            
        }
    }
};
```
performance

| Runtime | Memory  |
| ------- | ------- |
| 60 ms	  | 35.6 MB |
