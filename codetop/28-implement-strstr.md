### 28. 实现 strStr()

> 题目

[链接](https://leetcode-cn.com/problems/implement-strstr/)

> 思路

暴力破解，匹配字符串

> 代码

```js
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function (haystack, needle) {
    let L = needle.length;
    let n = haystack.length;
    for (let start = 0; start < n - L + 1; start++) {
        if (haystack.substring(start, start + L) === needle) {
            return start;
        }
    }
    return -1;
};
```

> 复杂度分析

时间复杂度：O(N - L)。

空间复杂度：O(1)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了59.65%的用户

内存消耗：38.9 MB, 在所有 JavaScript 提交中击败了37.63%的用户
