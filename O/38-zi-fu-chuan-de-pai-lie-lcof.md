### 剑指 Offer 38. 字符串的排列

> 题目

[链接](https://leetcode-cn.com/problems/zi-fu-chuan-de-pai-lie-lcof/)

> 思路

固定头字符，再与剩余字符的组合，使用递归。

> 代码

```js
/**
 * @param {string} s
 * @return {string[]}
 */
var permutation = function (s) {
    const len = s.length;

    if (len === 1) return [s];

    let res = new Set();
    for (let i = 0; i < len; i++) {
        const firstStr = s.charAt(i);
        const restStr = s.substr(0, i) + s.substr(i + 1);
        const restList = permutation(restStr);
        restList.forEach(str => {
            res.add(`${firstStr}${str}`)
        })
    }

    return Array.from(res);
};
```

> 复杂度分析

时间复杂度：O(N!)。

空间复杂度：O(N ^ 2)。

> 执行

执行用时：212 ms, 在所有 JavaScript 提交中击败了29.67%的用户

内存消耗：48.4 MB, 在所有 JavaScript 提交中击败了30.08%的用户