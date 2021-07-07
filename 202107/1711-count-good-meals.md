### 1711. 大餐计数

> 题目

[链接](https://leetcode-cn.com/problems/count-good-meals/)

> 思路

哈希表

> 代码

```js
/**
 * @param {number[]} deliciousness
 * @return {number}
 */
var countPairs = function(deliciousness) {
    const MOD = 1000000007;
    let maxVal = 0;
    for (const val of deliciousness) {
        maxVal = Math.max(maxVal, val);
    }
    const maxSum = maxVal * 2;
    let pairs = 0;
    const map = new Map();
    const n = deliciousness.length;
    for (let i = 0; i < n; i++) {
        const val = deliciousness[i];
        for (let sum = 1; sum <= maxSum; sum <<= 1) {
            const count = map.get(sum - val) || 0;
            pairs = (pairs + count) % MOD;
        }
        map.set(val, (map.get(val) || 0) + 1);
    }
    return pairs;
};
```

> 复杂度分析

时间复杂度：O(nlogC)。n是数组长度，C是数组值上限

空间复杂度：O(n)。

> 执行

执行用时：260 ms, 在所有 JavaScript 提交中击败了86.54%的用户

内存消耗：50.8 MB, 在所有 JavaScript 提交中击败了92.31%的用户