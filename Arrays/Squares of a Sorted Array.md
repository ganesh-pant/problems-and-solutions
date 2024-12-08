# Squares of a Sorted Array

Given an integer array nums sorted in **non-decreasing order**, return an array of **the squares of each number** sorted in non-decreasing order.

**Example 1:**
```
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```
**Example 2:**
```
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
 ```

**Constraints:**

* 1 <= nums.length <= 104
* -104 <= nums[i] <= 104
* nums is sorted in non-decreasing order.

# Solution
* Two Pointer
* Since the array A is sorted, loosely speaking it has some negative elements with squares in decreasing order, then some non-negative elements with squares in increasing order.
For example, with [-3, -2, -1, 4, 5, 6], we have the negative part [-3, -2, -1] with squares [9, 4, 1], and the positive part [4, 5, 6] with squares [16, 25, 36]. Our strategy is to iterate over the negative part in reverse, and the positive part in the forward direction.


* We can use two pointers to read the positive and negative parts of the array - one pointer j in the positive direction, and another i in the negative direction.

* Now that we are reading two increasing arrays (the squares of the elements), we can merge these arrays together using a two-pointer technique.
```
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var sortedSquares = function(nums) {
    var retArr = [];
    
    var len = nums.length;
    var left = 0;
    var right = len -1;
    var item = 0
    for(var i= len-1; i >= 0; i--){
        if(Math.abs(nums[left]) < Math.abs(nums[right])){
            item = nums[right];
            right --; 
        } else {
            item = nums[left];
            left ++;      
        }
        
        retArr[i] = item * item;
    }
    
    return retArr;
};
```

**Complexity Analysis**

* Time Complexity: O(N), where N is the length of A.

* Space Complexity: O(N) if you take output into account and O(1) otherwise.
