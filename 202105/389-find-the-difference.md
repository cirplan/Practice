### 389. 找不同

> 题目

[链接](https://leetcode-cn.com/problems/find-the-difference/)

> 思路

使用数组记录

> 代码

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {character}
 */
var findTheDifference = function (s, t) {
    const cnt = new Array(26).fill(0);
    for (const ch of s) {
        cnt[ch.charCodeAt() - 'a'.charCodeAt()]++;
    }
    for (const ch of t) {
        cnt[ch.charCodeAt() - 'a'.charCodeAt()]--;
        if (cnt[ch.charCodeAt() - 'a'.charCodeAt()] < 0) {
            return ch;
        }
    }
    return ' ';
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了62.68%的用户

内存消耗：39.4 MB, 在所有 JavaScript 提交中击败了54.70%的用户

