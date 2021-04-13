### 22. 括号生成

> 题目

[链接](https://leetcode-cn.com/problems/generate-parentheses/)

> 思路

？

> 代码

```js
/**
 * @param {number} n
 * @return {string[]}
 */
var generateParenthesis = function (n) {
    const res = []
    function dfs(l, r, str) {
        if (l == n && r == n) {
            return res.push(str)
        }
        if (l < r)
            return
        if (l < n) {
            dfs(l + 1, r, str + '(')
        }
        if (r < l) {
            dfs(l, r + 1, str + ')')
        }
    }

    dfs(0, 0, '')
    return res
};
```

> 复杂度分析

时间复杂度：?。

空间复杂度：?。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了56.44%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了61.58%的用户