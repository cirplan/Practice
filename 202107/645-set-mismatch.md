### 645. 错误的集合

> 题目

[链接](https://leetcode-cn.com/problems/set-mismatch/)

> 思路

排序后取值

> 代码

```js
/**
 * @param {number[]} nums
 * @return {number[]}
 */
var findErrorNums = function (nums) {
    const errorNums = new Array(2).fill(0);
    const n = nums.length;
    nums.sort((a, b) => a - b);
    let prev = 0;
    for (let i = 0; i < n; i++) {
        const curr = nums[i];
        if (curr === prev) {
            errorNums[0] = prev;
        } else if (curr - prev > 1) {
            errorNums[1] = prev + 1;
        }
        prev = curr;
    }
    if (nums[n - 1] !== n) {
        errorNums[1] = n;
    }
    return errorNums;
};
```

> 复杂度分析

时间复杂度：O(logN)。

空间复杂度：O(1)。

> 执行

执行用时：132 ms, 在所有 JavaScript 提交中击败了32.09%的用户

内存消耗：41.5 MB, 在所有 JavaScript 提交中击败了44.99%的用户



