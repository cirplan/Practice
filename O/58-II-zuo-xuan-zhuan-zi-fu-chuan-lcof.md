### 剑指 Offer 58 - II. 左旋转字符串

> 题目

[链接](https://leetcode-cn.com/problems/zuo-xuan-zhuan-zi-fu-chuan-lcof/)

> 思路

字符串拼接

> 代码

```js
/**
 * @param {string} s
 * @param {number} n
 * @return {string}
 */
var reverseLeftWords = function(s, n) {
    let s1 = s.substr(0, n);
    let s2 = s.substr(n);
    return s2 + s1;
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：88 ms, 在所有 JavaScript 提交中击败了45.70%的用户

内存消耗：39.3 MB, 在所有 JavaScript 提交中击败了49.32%的用户
