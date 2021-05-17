### 704. 二分查找

> 题目

[链接](https://leetcode-cn.com/problems/binary-search/)

> 思路

二分

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function(nums, target) {
    const len = nums.length;
    if (len === 0) return -1;

    let left = 0; 
    let right = len - 1;
    while (left <= right) {
        const mid = left + parseInt((right - left) / 2);
        const num = nums[mid];
        if (target === num) {
            return mid;
        } else if (target < num) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }

    return -1;
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了70.07%的用户

内存消耗：41.6 MB, 在所有 JavaScript 提交中击败了5.31%的用户
