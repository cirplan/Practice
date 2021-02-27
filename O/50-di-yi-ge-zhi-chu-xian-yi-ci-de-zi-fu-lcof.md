### 剑指 Offer 50. 第一个只出现一次的字符

> 题目

[链接](https://leetcode-cn.com/problems/di-yi-ge-zhi-chu-xian-yi-ci-de-zi-fu-lcof/)

> 思路

循环两次，第一次记录字符出现次数，第二次判断字符次数是否为1。

> 代码

```js
/**
 * @param {string} s
 * @return {character}
 */
var firstUniqChar = function(s) {
    if (!s.length) {
        return ' ';
    }

    let strs = {};

    for (let i = 0; i < s.length; i++) {
        const _s = s.charAt(i);
        strs[_s] = (strs[_s] || 0) + 1;
    }

    for (let i = 0; i < s.length; i++) {
        const _s = s.charAt(i);
        if (strs[_s] === 1) {
            return _s;
        }
    }

    return ' ';
};
```

> 复杂度分析

时间复杂度：O(N)。

空间复杂度：O(N)。

> 执行

执行用时：120 ms, 在所有 JavaScript 提交中击败了73.86%的用户

内存消耗：41.5 MB, 在所有 JavaScript 提交中击败了31.42%的用户
