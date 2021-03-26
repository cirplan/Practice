### 面试题 01.09. 字符串轮转

> 题目

[链接](https://leetcode-cn.com/problems/string-rotation-lcci/)

> 思路

s2 + s1 ，包含s1

> 代码

```js
/**
 * @param {string} s1
 * @param {string} s2
 * @return {boolean}
 */
var isFlipedString = function (s1, s2) {
    const len1 = s1.length;
    const len2 = s2.length;
    if (len1 !== len2) {
        return false;
    }

    return (s2 + s2).includes(s1);
};
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：72 ms, 在所有 JavaScript 提交中击败了96.63%的用户

内存消耗：39.2 MB, 在所有 JavaScript 提交中击败了53.93%的用户