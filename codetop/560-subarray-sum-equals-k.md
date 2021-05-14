### 560. 和为K的子数组

> 题目

[链接](https://leetcode-cn.com/problems/subarray-sum-equals-k/)

> 思路

？？

> 代码

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var subarraySum = function (nums, k) {
    const mp = new Map();
    mp.set(0, 1);
    let count = 0, pre = 0;
    for (const x of nums) {
        pre += x;
        if (mp.has(pre - k)) {
            count += mp.get(pre - k);
        }
        if (mp.has(pre)) {
            mp.set(pre, mp.get(pre) + 1);
        } else {
            mp.set(pre, 1);
        }
    }
    return count;
};
```

> 复杂度分析

时间复杂度：O(n)。

空间复杂度：O(n)。

> 执行

执行用时：100 ms, 在所有 JavaScript 提交中击败了95.79%的用户

内存消耗：46.7 MB, 在所有 JavaScript 提交中击败了57.53%的用户