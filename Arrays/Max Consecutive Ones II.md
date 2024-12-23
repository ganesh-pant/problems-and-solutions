# Max Consecutive Ones II

Given a binary array nums, return the maximum number of consecutive 1's in the array if you can flip at most one 0.

**Example 1:**
```
Input: nums = [1,0,1,1,0]
Output: 4
Explanation: 
- If we flip the first zero, nums becomes [1,1,1,1,0] and we have 4 consecutive ones.
- If we flip the second zero, nums becomes [1,0,1,1,1] and we have 3 consecutive ones.
The max number of consecutive ones is 4.
```
**Example 2:**
```
Input: nums = [1,0,1,1,0,1]
Output: 4
Explanation: 
- If we flip the first zero, nums becomes [1,1,1,1,0,1] and we have 4 consecutive ones.
- If we flip the second zero, nums becomes [1,0,1,1,1,1] and we have 4 consecutive ones.
The max number of consecutive ones is 4.
 ```

**Constraints:**

* 1 <= nums.length <= 105
* nums[i] is either 0 or 1.

# Solution (Javascript)
* one pointer: track two sets of ones, current set and previous set, resetting previous to 0 if 2 consecutive 0s are encountered. Add 1 if at least one 0 is encountered:

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var findMaxConsecutiveOnes = function(nums) {
    var max = 0;
    var curr = 0, prev = 0, seenZero = 0;
    
    for (var i = 0; i < nums.length; i++) {
        if (nums[i] == 0) {
            seenZero = 1;
            prev = curr;
            curr = 0;
        } else {
            curr++;
        }
        
        max = Math.max(max, curr + prev + seenZero);
    }

    return max;
};
```
