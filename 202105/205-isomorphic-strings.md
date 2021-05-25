### 205. 同构字符串

> 题目

[链接](https://leetcode-cn.com/problems/isomorphic-strings/)

> 思路

使用map辅助

> 代码

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function (s, t) {
    const s2t = {};
    const t2s = {};
    const len = s.length;
    for (let i = 0; i < len; ++i) {
        const x = s[i], y = t[i];
        if ((s2t[x] && s2t[x] !== y) || (t2s[y] && t2s[y] !== x)) {
            return false;
        }
        s2t[x] = y;
        t2s[y] = x;
    }
    return true;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：92 ms, 在所有 JavaScript 提交中击败了82.31%的用户

内存消耗：39.7 MB, 在所有 JavaScript 提交中击败了58.61%的用户
