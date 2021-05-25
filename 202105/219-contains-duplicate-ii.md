### 219. 存在重复元素 II

> 题目

[链接](https://leetcode-cn.com/problems/contains-duplicate-ii/)

> 思路

使用set辅助

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {boolean}
 */
var containsNearbyDuplicate = function (nums, k) {
    const set = new Set();
    for (let i = 0; i < nums.length; i++) {
        if (set.has(nums[i])) {
            return true;
        }
        set.add(nums[i]);
        if (set.size > k) {
            set.delete(nums[i - k]);
        }
    }
    return false;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：96 ms, 在所有 JavaScript 提交中击败了74.41%的用户

内存消耗：42.3 MB, 在所有 JavaScript 提交中击败了65.61%的用户
