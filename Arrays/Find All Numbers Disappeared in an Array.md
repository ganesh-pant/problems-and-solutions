# Find All Numbers Disappeared in an Array

Given an array nums of n integers where nums[i] is in the range [1, n], return an array of all the integers in the range [1, n] that do not appear in nums.

 

**Example 1:**
```
Input: nums = [4,3,2,7,8,2,3,1]
Output: [5,6]
```

**Example 2:**
```
Input: nums = [1,1]
Output: [2]
```

**Constraints:**

* n == nums.length
* 1 <= n <= 105
* 1 <= nums[i] <= n

# Solution (Javascript)
* Using Hash Map?
* The intuition behind using a hash map is pretty clear in this case. We are given that the array would be of size N and it should contain numbers from 1 to N. However, some of the numbers are missing. All we have to do is keep track of which numbers we encounter in the array and then iterate from 1⋯N and check which numbers did not appear in the hash table. Those will be our missing numbers.
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findDisappearedNumbers = function(nums) {
     var retArr = [];

    var map = new Map();
    for(var i=0; i <= nums.length - 1 ;i++) {
        map[nums[i]] = true;
    }

    for(var i=0; i <= nums.length - 1 ;i++) {
        var expectedItem = i+1;
        if (!map[expectedItem]) {
            retArr.push(expectedItem);
        }
    }
    
    return retArr;
};
```
