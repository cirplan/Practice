### 剑指 Offer 58 - I. 翻转单词顺序

> 题目

[链接](https://leetcode-cn.com/problems/fan-zhuan-dan-ci-shun-xu-lcof/)

> 思路

使用双指针，从后往前。

> 代码

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseWords = function (s) {
    s = s.trim();
    let j = s.length - 1;
    let i = j;
    let res = [];
    while (i >= 0) {
        while (i >= 0 && s.charAt(i) != ' ') i--;
        res.push(s.substring(i + 1, j + 1));
        while (i >= 0 && s.charAt(i) == ' ') i--;
        j = i;
    }
    return res.join(' '); // 转化为字符串并返回
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：80 ms, 在所有 JavaScript 提交中击败了81.56%的用户

内存消耗：39.8 MB, 在所有 JavaScript 提交中击败了14.95%的用户
