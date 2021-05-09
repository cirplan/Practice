### 771. 宝石与石头

> 题目

[链接](https://leetcode-cn.com/problems/jewels-and-stones/)

> 思路

暴力或哈希

> 代码

```js
/**
 * @param {string} jewels
 * @param {string} stones
 * @return {number}
 */
var numJewelsInStones = function (jewels, stones) {
    const jewelsSet = new Set(jewels.split(''));
    return stones.split('').reduce((prev, val) => {
        return prev + jewelsSet.has(val);
    }, 0);
};
```

> 复杂度分析

时间复杂度：O(m+n)。

空间复杂度：O(m)。

> 执行

执行用时：76 ms, 在所有 JavaScript 提交中击败了96.69%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了36.98%的用户
