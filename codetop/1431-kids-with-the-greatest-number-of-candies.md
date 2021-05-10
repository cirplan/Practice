### 1431. 拥有最多糖果的孩子

> 题目

[链接](https://leetcode-cn.com/problems/kids-with-the-greatest-number-of-candies/)

> 思路

先找出最大，再分别对比

> 代码

```js
/**
 * @param {number[]} candies
 * @param {number} extraCandies
 * @return {boolean[]}
 */
var kidsWithCandies = function (candies, extraCandies) {
    let n = candies.length;
    let maxCandies = 0;
    for (let i = 0; i < n; ++i) {
        maxCandies = Math.max(maxCandies, candies[i]);
    }
    let ret = [];
    for (let i = 0; i < n; ++i) {
        ret.push(candies[i] + extraCandies >= maxCandies);
    }
    return ret;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了58.42%的用户

内存消耗：39.1 MB, 在所有 JavaScript 提交中击败了34.82%的用户
