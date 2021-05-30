### 459. 重复的子字符串

> 题目

[链接](https://leetcode-cn.com/problems/repeated-substring-pattern/)

> 思路

循环

> 代码

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function (s) {
    let s1 = (s + s).slice(1, -1);
    return s1.indexOf(s) != -1;
};
```

> 复杂度分析

时间复杂度：O(1)。

空间复杂度：O(1)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了95.89%的用户

内存消耗：40.1 MB, 在所有 JavaScript 提交中击败了91.96%的用户
