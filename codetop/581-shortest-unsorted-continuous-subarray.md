### 581. 最短无序连续子数组

> 题目

[链接](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/)

> 思路

先排序，后对比

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var findUnsortedSubarray = function (nums) {
    let snums = nums.slice();
    snums = snums.sort((a, b) => a - b);
    let start = snums.length, end = 0;
    for (let i = 0; i < snums.length; i++) {
        if (snums[i] != nums[i]) {
            start = Math.min(start, i);
            end = Math.max(end, i);
        }
    }
    return (end - start >= 0 ? end - start + 1 : 0);
};
```

> 复杂度分析

时间复杂度：O(nlogn)。

空间复杂度：O(n)。

> 执行

执行用时：120 ms, 在所有 JavaScript 提交中击败了47.74%的用户

内存消耗：42.3 MB, 在所有 JavaScript 提交中击败了21.61%的用户
