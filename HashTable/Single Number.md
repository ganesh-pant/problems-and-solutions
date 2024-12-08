# Single Number
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

 
**Example 1:**
```
Input: nums = [2,2,1]
Output: 1
```
**Example 2:**
```
Input: nums = [4,1,2,1,2]
Output: 4
```
**Example 3:**
```
Input: nums = [1]
Output: 1
 ```

**Constraints:**

* 1 <= nums.length <= 3 * 104
* -3 * 104 <= nums[i] <= 3 * 104
* Each element in the array appears twice except for one element which appears only once.

# Solution (Javascript)

## 1. **HashTable** 
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
        let hash_table = {};
    for (let num of nums) {
        if (hash_table[num]) {
            hash_table[num]++;
        } else {
            hash_table[num] = 1;
        }
    }
    for (let num of nums) {
        if (hash_table[num] == 1) {
            return num;
        }
    }
    return 0;
};
```
Complexity Analysis

* Time complexity : O(n⋅1)=O(n). Time complexity of for loop is O(n). Time complexity of hash table(dictionary in python) operation pop is O(1).

* Space complexity : O(n). The space required by hash_table is equal to the number of elements in nums.
 
## 2. Math 
```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
    let setSum = 0,
        numsSum = 0;
    const set = new Set();
    for (const num of nums) {
        if (!set.has(num)) {
            set.add(num);
            setSum += num;
        }
        numsSum += num;
    }
    return 2 * setSum - numsSum;
};
```
Complexity Analysis

* Time complexity : O(n+n)=O(n). sum will call next to iterate through nums. We can see it as sum(list(i, for i in nums)) which means the time complexity is O(n) because of the number of elements(n) in nums.
* Space complexity : O(n+n)=O(n). set needs space for the elements in nums

## 3. Bit Manipulation (Best)
Concept

If we take XOR of zero and some bit, it will return that bit
a⊕0=a
If we take XOR of two same bits, it will return 0
a⊕a=0
a⊕b⊕a=(a⊕a)⊕b=0⊕b=b
So we can XOR all bits together to find the unique number.

```
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
    let a = 0;
    for (let i of nums) {
        a ^= i;
    }
    return a;
};
```
Complexity Analysis

* Time complexity : O(n). We only iterate through nums, so the time complexity is the number of elements in nums.

* Space complexity : O(1).
