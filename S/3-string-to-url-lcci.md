### 面试题 01.03. URL化

> 题目

[链接](https://leetcode-cn.com/problems/string-to-url-lcci/)

> 思路

循环匹配

> 代码

```js
/**
 * @param {string} S
 * @param {number} length
 * @return {string}
 */
var replaceSpaces = function (S, length) {
    let res = [];
    for (let i = 0; i < length; i++) {
        const _s = S[i];
        if (_s !== ' ') {
            res.push(_s);
        } else {
            res.push('%20');
        }
    }

    return res.join('');
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：168 ms, 在所有 JavaScript 提交中击败了46.09%的用户

内存消耗：71.2 MB, 在所有 JavaScript 提交中击败了9.38%的用户
