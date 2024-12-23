# Intersection of Two Arrays
Given two integer arrays nums1 and nums2, return an array of their intersection. Each element in the result must be unique and you may return the result in any order.

**Example 1:**
```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
```
**Example 2:**
```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
 ```

**Constraints:**

* 1 <= nums1.length, nums2.length <= 1000
* 0 <= nums1[i], nums2[i] <= 1000

# Solution (Javascript)
  ```
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    let hashSetNum1 = new Set(nums1);
    let hashSetNum2 = new Set(nums2);

    const getIntersecton = (set1, set2) => {
        values = [];
        for(let v of set1){
            if(set2.has(v)){
               values.push(v);
            }
        }
        return values;
    }

    if (hashSetNum1.size < hashSetNum2.size) {
        return getIntersecton(hashSetNum1, hashSetNum2)
    } else {
        return getIntersecton(hashSetNum2, hashSetNum1)
    }
};
  ```
