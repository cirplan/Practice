### 930. 和相同的二元子数组

> 题目

[链接](https://leetcode-cn.com/problems/binary-subarrays-with-sum/)

> 思路

哈希表

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} goal
 * @return {number}
 */
var numSubarraysWithSum = function (nums, goal) {
    let sum = 0;
    const cnt = new Map();
    let ret = 0;
    for (const num of nums) {
        cnt.set(sum, (cnt.get(sum) || 0) + 1);
        sum += num;
        ret += cnt.get(sum - goal) || 0;
    }
    return ret;
};

```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了100.00%的用户

内存消耗：44.8 MB, 在所有 JavaScript 提交中击败了29.09%的用户