### 34. 在排序数组中查找元素的第一个和最后一个位置

> 题目

[链接](https://leetcode-cn.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

> 思路

二分法

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var searchRange = function (nums, target) {
    const len = nums.length;
    if (!len) return [-1, -1];

    let left = 0;
    let right = len - 1;
    while (left <= right) {
        const mid = left + parseInt((right - left) / 2);
        const num = nums[mid];
        if (num > target) {
            right = mid - 1;
        } else if (num < target) {
            left = mid + 1;
        } else {
            let start = mid;
            while (start > 0 && nums[start - 1] === target) {
                start--;
            }
            let end = mid;
            while (end < len - 1 && nums[end + 1] === target) {
                end++;
            }
            return [start, end];
        }
    }

    return [-1, -1];
};
```

> 复杂度分析

时间复杂度：O(logn)。

空间复杂度：O(1)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了36.45%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了60.30%的用户
