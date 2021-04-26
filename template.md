### 647. 回文子串

> 题目

[链接](https://leetcode-cn.com/problems/palindromic-substrings/)

> 思路

??

> 代码

```js
/**
 * @param {string} s
 * @return {number}
 */
var countSubstrings = function (s) {
    const n = s.length;
    let ans = 0;
    for (let i = 0; i < 2 * n - 1; ++i) {
        let l = i / 2, r = i / 2 + i % 2;
        while (l >= 0 && r < n && s.charAt(l) == s.charAt(r)) {
            --l;
            ++r;
            ++ans;
        }
    }
    return ans;
};

```

> 复杂度分析

时间复杂度：O(N ^ 2)。

空间复杂度：O(1)。

> 执行

执行用时：104 ms, 在所有 JavaScript 提交中击败了67.63%的用户

内存消耗：43.6 MB, 在所有 JavaScript 提交中击败了56.73%的用户
